<script lang="ts">
	import ProfilePic from '$lib/imgs/image-jeremy.png';
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

<div class="wrapper">
	<div class="dashboard">
		<div class="dashboard-profile">
			<img src={ProfilePic} alt="" />
			<span class="text">
				<p>Report for</p>
				<p class="profile-name">Jeremy Robson</p>
			</span>
		</div>
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
</div>

<style lang="scss">
	.wrapper {
		display: flex;
		flex-direction: row;
		gap: 1rem;
	}
	.dashboard {
		width: 225px;
		overflow: hidden;
		position: relative;
		z-index: 1;
		display: grid;
		grid-template-rows: 1fr auto;
		&-profile {
			padding: 2rem;
			border-radius: 1rem;
			background-color: $blue-400;
			display: flex;
			flex-direction: column;
			justify-content: space-evenly;
			img {
				border: 2px solid white;
				border-radius: 50%;
				max-width: 80px;
			}
			p {
				color: $blue-300;
				font-weight: 400;
				font-size: 18px;
			}
			.profile-name {
				color: white;
				font-size: 2rem;
				font-weight: 300;
			}
		}
		&-selector {
			position: relative;
			z-index: -1;
			margin-top: -0.75rem;
			padding-top: 3rem;
			padding: 2rem;
			border-bottom-left-radius: 1rem;
			border-bottom-right-radius: 1rem;
			display: flex;
			flex-direction: column;
			gap: 1rem;
			font-weight: 300;
			background-color: $blue-600;
			input[type='radio'] {
				opacity: 0;
				position: fixed;
				width: 0;
			}
			label {
				color: $blue-300;
			}
			[type='radio']:checked + label {
				color: white;
			}
			[type='radio']:hover + label {
				color: white;
				cursor: pointer;
			}
		}
	}
	.timecard-wrapper {
		width: 825px;
		display: flex;
		flex-wrap: wrap;
		flex-direction: row;
		gap: 1rem;
	}
</style>
