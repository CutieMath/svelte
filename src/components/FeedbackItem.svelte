<script>
    import { createEventDispatcher } from 'svelte';
    import Card from '../UI/Card.svelte'; 
    export let item;
    const dispatch = createEventDispatcher();
    
    const handleDelete = (itemId) => {
        dispatch('delete-item', itemId)
    }
</script>

<!-- Use Slots -->
<Card>
    <div class="num-display">
        {item.rating}
    </div>
    <button class="close-button" on:click={() => handleDelete(item.id)}>X</button>
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
        background: #EBA5B0;
        color: #fff;
        border: 1px #fff solid;
        border-radius: 50%;
        padding: 10px;
        text-align: center;
        font-size: 19px;
        box-shadow: rgba(0, 0, 0, 0.08) 0px 4px 12px;
    }
    .close-button {
        position: absolute;
        top: 10px;
        right: 20px;
        cursor: pointer;
        background: none;
        border: none;
    }
</style>