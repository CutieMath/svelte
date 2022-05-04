<script>
    import Card from '../UI/Card.svelte'; 
    export let item;
</script>

<!-- Use Slots -->
<Card>
    <div class="num-display">
        {item.rating}
    </div>
    <div class="close-button">x</div>
    <p class="text-display">
        {item.content}
    </p>
</Card>

<style>
    .num-display {
        position: absolute;
        top: -10px;
        left: -10px;
        width: 50px;
        height: 50px;
        background: #D291BC;
        color: #fff;
        border: 1px #eee solid;
        border-radius: 50%;
        padding: 10px;
        text-align: center;
        font-size: 19px;
    }
    .close-button {
        position: absolute;
        top: 10px;
        right: 20px;
        cursor: pointer;
    }
</style>