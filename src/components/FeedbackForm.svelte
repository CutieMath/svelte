<script>
    import Card from '../UI/Card.svelte'
    import Button from '../UI/Button.svelte'
    import RatingSelect from './RatingSelect.svelte'
    
    let btnDisabled = true
    let text = ''
    let message
    let rating = 10
    const MIN = 10

    const handleInput = () => {
        if(text.trim().length <= MIN){
            message = `Text must be at least ${MIN} characters`
            btnDisabled = true            
        } else {
            message = null 
            btnDisabled = false 
        }
    }
</script>

<Card>
    <header>
        <h2>How would you rate your user experience?</h2>
    </header>
    <form>
        <RatingSelect />
        <div class="input-group">
            <input type="text" on:input={handleInput} bind:value={text} placeholder="Tell me a secret x">
            <Button disabled={btnDisabled} type="submit">Send</Button>
        </div>
        {#if message}
            <div class="message">
                {message}
            </div>
        {/if}
    </form>
</Card>


<style>
  header {
    max-width: 400px;
    margin: auto;
  }
  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }
  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }
  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }
  input:focus {
    outline: none;
  }
  .message{
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>