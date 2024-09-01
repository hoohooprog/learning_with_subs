
<script>
    import { onMount } from 'svelte';
    // import SubtitleEditor from '$lib/SubtitleEditor.svelte';
    import VideoPlayer from '$lib/VideoPlayer.svelte';
    // import { fetchSubtitles } from '$lib/api.js';
  
    //export let params;
    let videoData = null;
    let subtitles = [];
    let isLoading = true;
    let videoUrl = null;

    
    $: alert(`video url is ${videoData}`);
    
    
  
    onMount(async () => {
      const urlParams = new URLSearchParams(location.search);
      // const startTime = urlParams.get('startTime');
      // const endTime = urlParams.get('endTime');
      // const subtitleStyle = urlParams.get('subtitleStyle');
      
      const url = urlParams.get('url');
      alert(`url is ${url}`);
      const videoUrl = decodeURIComponent(params.slug);
      
      // Fetch subtitles using backend API
      // subtitles = await fetchSubtitles(videoUrl, startTime, endTime, subtitleStyle);
      // Call backend API to process video and subtitles
    try {
      // const response = await fetchSubtitles(url);
      
      videoData = { videoUrl };
      isLoading = false;
    } catch (error) {
      console.error('Error processing video:', error);
      // Handle error (show message to user)
    } 
    });
    
  </script>

{@debug isLoading, videoUrl}

  
  <main>
    {#if isLoading}
      <div>Loading video...</div>
    {:else}
      <VideoPlayer {videoData} />
      
    {/if}
  </main>
  