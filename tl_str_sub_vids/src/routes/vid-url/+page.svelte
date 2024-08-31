<!--
    vid-url.svelte acts as a page to accept user vid selection
    and options associated with viewing.

    we present 2 options: 
    1) karaoke-style for following of audio stream
    &
    2) multi-lingual block style subtitles for reference and comparison

    1st iteration will be without time-marker selection for video. 
    Hence any video selected will be trimmed to the first 5 minutes

    for testing purposes, translations will default to English, because by default
    Whisper's purpose is to translate languages to English.

-->


<script>
    import { goto } from '$app/navigation';
    let url = '';
    // let startTime = 0;
    // let endTime = 300; // Maximum of 5 mins
    let subtitleStyle = 'karaoke';
    let languages = ['en']; // Default English

    function submit() {
        const params = new URLSearchParams({
            url,
            //startTime,
            //endTime,
            subtitleStyle
        });
        console.log(params);
        // Redirect to the videoplayer with parameters in the query string
        goto(`/videoplayer/${encodeURIComponent(url)}`);
    }
</script>

<nav>
    <a href="/">home</a>
    <a href="/vid-url">translate a video</a>
</nav>

<main>
    <h1>Enter video URL</h1>
    <input type="text" bind:value={url} placeholder="URL link" />

    <h2>Subtitle Options</h2>

    <label for="subtitle style">Subtitle Style:</label>
    <select bind:value={subtitleStyle}>
        <option value="karaoke">Karaoke style</option>
        <option value="multilingual">Multilingual Subtitles</option>
    </select>

    
    {#if subtitleStyle === 'karaoke'}
        <label for="Select language">Select language:</label>

        <input 
            id="language" 
            type="text" 
            bind:value={languages} 
            placeholder="Enter language (e.g., en)"
        />
    {/if}


    {#if subtitleStyle === 'multilingual'}
        <label for="Select languages">Select languages:</label>

        <input type="text" bind:value={languages[0]} placeholder="Language 1 (e.g., en)" />
        <input type="text" bind:value={languages[1]} placeholder="Language 2 (e.g., es)" />
        <input type="text" bind:value={languages[2]} placeholder="Language 3 (e.g., fr)" />
    {/if}

    <button on:click={submit}>Submit</button>



</main>

<style>
    main {
      padding: 1rem;
    }
    input, select, button {
      margin: 0.5rem 0;
    }
  </style>
  