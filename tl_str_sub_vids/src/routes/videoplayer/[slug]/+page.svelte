<script>
    import { onMount } from 'svelte';
    // import SubtitleEditor from '$lib/SubtitleEditor.svelte';
    import VideoPlayer from '$lib/VideoPlayer.svelte';
    // import { fetchSubtitles } from '$lib/api.js';
  
    export let params;
    let videoData = null;
    let subtitles = [];
    let isLoading = true;
    let videoUrl = null;

    
    
    
  
    onMount(async () => {
      // const urlParams = new URLSearchParams(location.search);
      // const startTime = urlParams.get('startTime');
      // const endTime = urlParams.get('endTime');
      // const subtitleStyle = urlParams.get('subtitleStyle');
      
      const videoUrl = decodeURIComponent(params.slug);
      
      // Fetch subtitles using backend API
      // subtitles = await fetchSubtitles(videoUrl, startTime, endTime, subtitleStyle);
      videoData = { url: videoUrl,};
      
      isLoading = false;
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
  