<script lang="ts">
	import Timecard from './Timecard.svelte';

	import Data_file from '$lib/data.json';
	const work_data = Data_file[0];
	const play_data = Data_file[1];
	const study_data = Data_file[2];
	const exercise_data = Data_file[3];
	const social_data = Data_file[4];
	const selfcare_data = Data_file[5];

	let selected_timeframe: 'daily' | 'weekly' | 'monthly' = 'daily';
</script>

<div class="dashboard">
	<div class="dashboard-profile" />
	<div class="dashboard-selector">
		<input
			type="radio"
			name="time"
			id="time-daily"
			bind:group={selected_timeframe}
			value={'daily'}
		/>
		<label for="time-daily"> Daily </label>

		<input
			type="radio"
			name="time"
			id="time-weekly"
			bind:group={selected_timeframe}
			value={'weekly'}
		/>
		<label for="time-weekly"> Weekly </label>

		<input
			type="radio"
			name="time"
			id="time-monthly"
			bind:group={selected_timeframe}
			value={'monthly'}
		/>
		<label for="time-monthly"> Monthly </label>
	</div>
</div>
<div class="timecard-wrapper">
	<Timecard category="work" cardData={work_data} {selected_timeframe} />

	<Timecard category="play" cardData={play_data} {selected_timeframe} />

	<Timecard category="study" cardData={study_data} {selected_timeframe} />

	<Timecard category="exercise" cardData={exercise_data} {selected_timeframe} />

	<Timecard category="social" cardData={social_data} {selected_timeframe} />

	<Timecard category="selfcare" cardData={selfcare_data} {selected_timeframe} />
</div>

<style lang="scss">
	.timecard-wrapper {
		width: 825px;
		display: flex;
		flex-wrap: wrap;
		flex-direction: row;
		gap: 1rem;
	}
	.dashboard-selector {
		display: flex;
		flex-direction: column;
		input[type='radio'] {
			opacity: 0;
			position: fixed;
			width: 0;
		}
		label {
			color: $blue-600;
		}
		[type='radio']:checked + label {
			color: $blue-200;
		}
	}
</style>
