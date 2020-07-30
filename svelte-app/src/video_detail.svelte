<script>
  export let video;
  let url = '';
  let videoId = '';
  $: if (video !== null) {
    videoId = video.id.videoId;
    url = `https://www.youtube.com/embed/${videoId}`;
  }
</script>

<style>
  .selected {
    margin: 2rem;
  }
  .details {
    width: 90%;
  }
  .title {
    font-size: 1.4rem;
    font-weight: bold;
  }
</style>

{#if !video}
  <div class="selected"></div>
{:else}
  <div class="selected">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe class="embed-responsive-item" src={url} title='video-detail' SameSite=None></iframe>
    </div>
      <div class="details">
        <div class="title">{video.snippet.title}</div>
        <div class="description">{video.snippet.description}</div>
      </div>
  </div>

  {/if}