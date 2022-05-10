<!-- Issue page: https://github.com/sveltejs/svelte/issues/4150 -->
<script>
	import FeedbackList from './components/FeedbackList.svelte';
	import FeedbackStats from './components/FeedbackStats.svelte';
	import FeedbackForm from './components/FeedbackForm.svelte';
</script>

<main class="container">
	<FeedbackForm/>
	<FeedbackStats/>
	<FeedbackList/>
</main>

<style>
</style>