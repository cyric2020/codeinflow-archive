<script>
    import { onMount } from 'svelte';
    import Video from '$lib/Video.svelte';
    
    var videos = [];

    onMount(async () => {
        const res = await fetch('/combined.json');
        const data = await res.json();
        console.log(data["data"]);
        videos = data["data"];
    });
</script>

<div class="container">
    <h1>CodeInFlow Videos</h1>

    <div class="videos">
        {#each videos as video}
            <Video {video} />
        {/each}
    </div>
</div>

<style>
    .container {
        width: 60%;
        margin: 2rem auto;
    }

    .videos {
        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
    }
</style>