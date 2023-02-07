<script lang="ts">
	/* Assets */
	import WorkIcon from '$lib/imgs/icon-work.svg';
	import PlayIcon from '$lib/imgs/icon-play.svg';
	import StudyIcon from '$lib/imgs/icon-study.svg';
	import ExerciseIcon from '$lib/imgs/icon-exercise.svg';
	import SocialIcon from '$lib/imgs/icon-social.svg';
	import SelfCareIcon from '$lib/imgs/icon-self-care.svg';
	import Dots from '$lib/imgs/icon-ellipsis.svg';

	/* Types */
	type cardObject = {
		title: string;
		timeframes: {
			daily: {
				current: number;
				previous: number;
			};
			weekly: {
				current: number;
				previous: number;
			};
			monthly: {
				current: number;
				previous: number;
			};
		};
	};
	type timeframe = 'daily' | 'weekly' | 'monthly';

	/* Props */
	export let cardData: cardObject;
	export let category: String;
	export let selected_timeframe: timeframe;

	/* Logic */
	let icon: string;
	if (category === 'work') {
		icon = WorkIcon;
	} else if (category === 'play') {
		icon = PlayIcon;
	} else if (category === 'study') {
		icon = StudyIcon;
	} else if (category === 'exercise') {
		icon = ExerciseIcon;
	} else if (category === 'social') {
		icon = SocialIcon;
	} else {
		icon = SelfCareIcon;
	}

	function getTime(selected_timeframe: timeframe, when: 'current' | 'previous') {
		if (when == 'current') return cardData.timeframes[selected_timeframe].current;
		else return cardData.timeframes[selected_timeframe].previous;
	}
	$: current_time = getTime(selected_timeframe, 'current');
	$: previous_time = getTime(selected_timeframe, 'previous');

	function getText(selected_timeframe: timeframe) {
		if (selected_timeframe == 'daily') return 'Yesterday';
		else if (selected_timeframe == 'weekly') return 'Last Week';
		else return 'Last Month';
	}
	$: previous_text = getText(selected_timeframe);
</script>

<div class="card">
	<div class="card-color {category}">
		<span class="card-icon">
			<img src={icon} alt="" class="icon" />
		</span>
	</div>
	<div class="card-info">
		<div class="card-info-heading">
			<h2>{cardData.title}</h2>
			<img src={Dots} alt="" />
		</div>
		<div class="card-info-stats">
			<p class="time-current">{current_time}hrs</p>
			<p class="time-previous">{previous_text} - {previous_time}hrs</p>
		</div>
	</div>
</div>

<style lang="scss">
	.card {
		border-radius: 1rem;
		overflow: hidden;
		@media (min-width: 900px) {
			width: 255px;
		}
		&-color {
			height: 60px;
			background-color: var(--bg-color);
			overflow: hidden;
			position: relative;
			z-index: -1;
		}
		&-icon {
			opacity: 60%;
			position: absolute;
			right: 1rem;
			top: 40%;
			transform: translateY(-40%);
		}
		&-info {
			color: white;
			background-color: $blue-600;
			margin-top: -1rem;
			border-radius: 1rem;
			padding: 2rem;
			font-size: 18px;
			&-heading {
				display: flex;
				flex-direction: row;
				align-items: center;
				justify-content: space-between;
			}
			&-stats {
				display: flex;
				flex-direction: row;
				align-items: center;
				justify-content: space-between;
				@media (min-width: 900px) {
					flex-wrap: wrap;
				}
			}

			h2 {
				font-size: 1rem;
				font-weight: 400;
				@media (min-width: 900px) {
					font-size: 1.5rem;
				}
			}
			&:hover {
				background-color: $blue-500;
				cursor: pointer;
			}
		}
	}
	.time-current {
		font-size: 24px;
		font-weight: 300;
		@media (min-width: 900px) {
			font-size: 3rem;
			font-weight: 300;
		}
	}
	.time-previous {
		font-weight: 300;
		font-size: 1rem;
		color: $blue-200;
		@media (min-width: 900px) {
			font-size: 18px;
		}
	}
	.work {
		--bg-color: #{$work-color};
	}
	.play {
		--bg-color: #{$play-color};
	}
	.study {
		--bg-color: #{$study-color};
	}
	.exercise {
		--bg-color: #{$exercise-color};
	}
	.social {
		--bg-color: #{$social-color};
	}
	.selfcare {
		--bg-color: #{$selfcare-color};
		.icon {
			transform: translateY(-7px);
		}
	}
</style>
