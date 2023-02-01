<script>
	import Timecard from './Timecard.svelte';
	import WorkIcon from '$lib/imgs/icon-work.svg';
	import PlayIcon from '$lib/imgs/icon-play.svg';
	import StudyIcon from '$lib/imgs/icon-study.svg';
	import ExerciseIcon from '$lib/imgs/icon-exercise.svg';

	import Data_file from '$lib/data.json';
	const work_data = Data_file[0];
	const play_data = Data_file[1];
	const study_data = Data_file[2];
	const exercise_data = Data_file[3];
</script>

<h1>Welcome to SvelteKit</h1>
<Timecard bgclass="work" cardData={work_data}>
	<img src={WorkIcon} alt="" slot="icon" />
</Timecard>

<Timecard bgclass="play" cardData={play_data}>
	<img src={PlayIcon} alt="" slot="icon" />
</Timecard>

<Timecard bgclass="study" cardData={study_data}>
	<img src={StudyIcon} alt="" slot="icon" />
</Timecard>

<Timecard bgclass="exercise" cardData={exercise_data}>
	<img src={ExerciseIcon} alt="" slot="icon" />
</Timecard>

<style lang="scss">
	h1 {
		color: $blue-400;
	}
</style>
