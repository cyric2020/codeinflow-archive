<script>
    export let video;

    console.log(video);

    function getTimeAgo(stringDate) {
        const date = new Date(stringDate);
        const now = new Date();
        const diff = now - date;

        const seconds = Math.floor(diff / 1000);
        const minutes = Math.floor(seconds / 60);
        const hours = Math.floor(minutes / 60);
        const days = Math.floor(hours / 24);
        const weeks = Math.floor(days / 7);
        const months = Math.floor(days / 30);
        const years = Math.floor(days / 365);

        if (seconds < 60) {
            return `${seconds} seconds ago`;
        } else if (minutes < 60) {
            return `${minutes} minutes ago`;
        } else if (hours < 24) {
            return `${hours} hours ago`;
        } else if (days < 7) {
            return `${days} days ago`;
        } else if (weeks < 4) {
            return `${weeks} weeks ago`;
        } else if (months < 12) {
            return `${months} months ago`;
        } else {
            return `${years} years ago`;
        }
    }
</script>

<div class="video">
    <img src={video.snippet.thumbnails.high.url} alt={video.snippet.title} />
    <div class="details">
        <p>{getTimeAgo(video.snippet.publishedAt)}</p>
        <h4>{video.snippet.title}</h4>
        <a href="https://www.youtube.com/watch?v={video.id.videoId}" target="_blank">🔗 Watch on YouTube</a>
    </div>
</div>

<style>
    .video {
        display: flex;
        flex-direction: column;
        margin-bottom: 2rem;
        min-width: 15rem;
        flex-basis: 0;
        flex-grow: 1;
        gap: 0.5rem;
    }

    .video img {
        width: 100%;
        border-radius: 0.5rem;
        aspect-ratio: 16 / 9;
        object-fit: cover;
    }

    .video .details {
        width: 100%;
    }

    .video .details h4 {
        font-weight: 600;
        margin: 0;
    }

    .video .details p {
        margin: 0;
        font-size: 0.8rem;
    }

    .video .details a {
        font-size: 0.8rem;
        color: #666;
        text-decoration: none;
    }
</style>