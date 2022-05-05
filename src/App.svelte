<script>
	import FeedbackList from './components/FeedbackList.svelte';
	import FeedbackStats from './components/FeedbackStats.svelte';

	let feedbacks = [
		{
			id: 1,
			rating: 9,
			content: 'To take a trivial example, which of us ever undertakes laborious physical exercise, except to obtain some advantage from it? But who has any right to find fault with a man who chooses to enjoy a pleasure that has no annoying consequences, or one who avoids a pain that produces no resultant pleasure?'
		},
		{
			id: 2,
			rating: 10,
			content: 'But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system, and expound the actual teachings of the great explorer of the truth, the master-builder of human happiness. No one rejects, dislikes, or avoids pleasure itself.'
		},
		{
			id: 3,
			rating: 10,
			content: 'On the other hand, we denounce with righteous indignation and dislike men who are so beguiled and demoralized by the charms of pleasure of the moment, so blinded by desire, that they cannot foresee the pain and trouble that are bound to ensue; and equal blame belongs to those who fail in their duty through weakness of will, which is the same as saying through shrinking from toil and pain.'
		}
	]

	$: itemCount = feedbacks.length;
	$: averageRate = Math.round(feedbacks.reduce((a, {rating}) => a + rating, 0) / feedbacks.length); 
	const deleteItem = (e) => {
		// get the item ID by e.detail
		const itemId = e.detail;
		feedbacks = feedbacks.filter((item) => item.id != itemId); 
	}
</script>

<main class="container">
	<FeedbackStats itemCount={itemCount} averageRate={averageRate}/>
	<FeedbackList feedbacks={feedbacks} on:delete-item={deleteItem}/>
</main>

<style>
</style>