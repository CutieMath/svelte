<script>
    export let itemCount 
    export let averageRate
</script>


<div class="feedback-stats">
    <h4>{itemCount} Reviews</h4>
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