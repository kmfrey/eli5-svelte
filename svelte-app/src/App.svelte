<script>
	import SearchBar from './search_bar.svelte';
	import VideoDetail from './video_detail.svelte';
	import VideoList from './video_list.svelte';
	import youtubeSearch from './youtube-api';
	// debounce taken from https://stackoverflow.com/questions/46104897/how-to-debounce-throttle-with-svelte Rich Harris's answer
	import { debounce } from 'lodash'

	let videos = [];
	let selectedVideo = null;
	let searchTerm='Pixar';

	// want to debounce the searching
	const searchYoutube = debounce(() => {
		youtubeSearch(searchTerm).then((videoList) => {
			videos = videoList;
			selectedVideo = videos[0];
		});
	}, 300);
		
	searchYoutube();

	function onSearchChange(event) {
		searchTerm = event.detail.searchTerm;
		searchYoutube();
	}
</script>

<style>
	.videos {
		display: flex;
		flex-direction: row;
	}

</style>

<SearchBar on:search={onSearchChange} {searchTerm}></SearchBar>
<div class="videos">
	<VideoDetail video={selectedVideo}></VideoDetail>
	<VideoList {videos} on:selected={(e) => selectedVideo = e.detail.video}></VideoList>
</div>
