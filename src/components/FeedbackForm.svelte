<script>
    import {v4 as uuidv4} from 'uuid'
    import {FeedbackStore} from '../stores'
    import Card from '../UI/Card.svelte'
    import Button from '../UI/Button.svelte'
    import RatingSelect from './RatingSelect.svelte'
    
    let btnDisabled = true
    let content = ''
    let message
    let rating = 10
    const MIN = 10
    const handleSelect = e => rating = e.detail
    const handleInput = () => {
        if(content.trim().length <= MIN){
            message = `Text must be at least ${MIN} characters`
            btnDisabled = true            
        } else {
            message = null 
            btnDisabled = false 
        }
    }
    const handleSubmit = () => {
      if(content.trim().length > MIN){
        const newFeedBack = {
          id: uuidv4(),
          content: content,
          rating: +rating
        }
        FeedbackStore.update((currentFeedback) => {
          return [newFeedBack, ...currentFeedback]
        })
        content = ""
      }
    }
</script>

<Card>
    <header>
        <h2>How would you rate your user experience with us?</h2>
    </header>
    <form on:submit|preventDefault={handleSubmit}>
        <RatingSelect on:rating-select={handleSelect}/>
        <div class="input-group">
            <input type="content" on:input={handleInput} bind:value={content} placeholder="Tell us your experience ...">
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
    color: #4C465D;
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
    text-align: left;
  }
</style>