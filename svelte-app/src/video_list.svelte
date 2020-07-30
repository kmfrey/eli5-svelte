<script>
  import VideoListItem from "./video_list_item.svelte";
  import { createEventDispatcher } from 'svelte';
  export let videos = [];
  const dispatch = createEventDispatcher();
</script>

<style>
	ul {
		list-style-type: none;
  }
</style>

<ul>
  {#if videos !== undefined}
    {#each videos as video}
      <VideoListItem key={video.etag} video={video} on:selected={(e) => dispatch('selected', {video: e.detail.video})}/>
    {/each}  
  {/if}
</ul>
