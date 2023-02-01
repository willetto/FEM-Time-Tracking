<script lang="ts">
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
	export let bgclass: String;
	export let cardData: cardObject;
</script>

<div class="card {bgclass}">
	<div class="card-color">
		<slot name="icon" />
	</div>
	<div class="card-info">
		<h1>{cardData.title}</h1>
	</div>
</div>

<style lang="scss">
	.card {
		&-color {
			padding: 2rem;
			background-color: var(--bg-color);
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
	}
</style>
