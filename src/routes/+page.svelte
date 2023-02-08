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
			<div class="text">
				<p>Report for</p>
				<p class="profile-name">Jeremy Robson</p>
			</div>
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
		flex-direction: column;
		gap: 1rem;
		@media (min-width: 900px) {
			flex-direction: row;
		}
	}
	.dashboard {
		width: 327px;
		overflow: hidden;
		z-index: 1;
		display: grid;
		@media (min-width: 900px) {
			grid-template-rows: 1fr auto;
			width: 225px;
		}
		&-profile {
			padding: 2rem;
			border-radius: 1rem;
			background-color: $blue-400;
			display: flex;
			justify-content: space-evenly;
			align-items: center;
			@media (min-width: 900px) {
				flex-direction: column;
				align-items: flex-start;
				justify-items: space-between;
			}
			img {
				border: 2px solid white;
				border-radius: 50%;
				max-width: 70px;
				@media (min-width: 900px) {
					max-width: 80px;
				}
			}
			p {
				color: $blue-200;
				font-weight: 400;
				font-size: 1rem;
				@media (min-width: 900px) {
					font-size: 18px;
				}
			}
			.profile-name {
				color: white;
				font-size: 24px;
				font-weight: 300;
				@media (min-width: 900px) {
					font-size: 2rem;
				}
			}
		}

		&-selector {
			background-color: $blue-600;
			position: relative;
			z-index: -1;
			margin-top: -0.75rem;
			height: 86px;
			padding: 2rem;
			padding-top: 2.2rem;
			border-bottom-left-radius: 1rem;
			border-bottom-right-radius: 1rem;
			display: flex;
			flex-direction: row;
			font-weight: 300;
			justify-content: space-between;
			@media (min-width: 900px) {
				flex-direction: column;
				gap: 1rem;
				padding-top: 3rem;
				height: unset;
			}
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
		display: flex;
		flex-wrap: wrap;
		flex-direction: column;
		gap: 1rem;
		@media (min-width: 900px) {
			flex-direction: row;
			width: 825px;
		}
	}
</style>
