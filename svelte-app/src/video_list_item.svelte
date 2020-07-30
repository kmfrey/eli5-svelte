<script>
  export let video;
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  const handleClick = () => {
    dispatch('selected', {video});
  }
  $: imgUrl = video.snippet.thumbnails.default.url;
  $: title = video.snippet.title;
</script>

<style>
  li {
    display: flex;
    margin: 0.5rem;
  }
  .title {
    padding:0.2rem;
  }
</style>

<li on:click={handleClick}>
  <img src={imgUrl} alt="video"/>
  <div class="title">{title}</div>
</li>