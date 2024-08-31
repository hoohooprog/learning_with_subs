<script>
    export let videoData;
    let videoSrc;
  
    $: if (videoData) {
      const videoId = new URL(videoData.url).searchParams.get('v');
      videoSrc = `https://www.youtube.com/embed/${videoId}`;
    }
  </script>
  
  <iframe
    src={videoSrc}
    title="video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    width="100%"
    height="500px">
  </iframe>
  