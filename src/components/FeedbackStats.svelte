<script>
    import {FeedbackStore} from '../stores'
	$: itemCount = $FeedbackStore.length;
	$: averageRate = Math.round($FeedbackStore.reduce((a, {rating}) => a + rating, 0) / $FeedbackStore.length); 
</script>


<div class="feedback-stats">
    {#if itemCount > 1}
        <h4>{itemCount} Reviews</h4>
    {:else}
        <h4>{itemCount} Review</h4>
    {/if}
    <h4>Ratings Average: {averageRate}</h4>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
        color: #4C4656;
        padding: 2%;
    }
</style>