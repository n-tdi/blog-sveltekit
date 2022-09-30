<script>
    export let date;
    export let title;
    export let tags;
    export let path;
</script>

<a href="{path}">
    <div class="post">
        <p class="date">{date}</p>
        <p class="post--title">{title}</p>
        <div class="post--tag">
            {#each tags as tag}
                <a class="tag" href="/tags/{tag}">#{tag}</a>
            {/each}
        </div>
    </div>
</a>

<style>
    a {
        text-decoration: none;
    }
    .post {
        padding: 10px 25px;
        margin-bottom: 20px;
        padding-top: 25px;
        border: 1px solid gray;
        border-radius: 20px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        transition: all 0.15s ease-in-out;
    }
    .post:hover {
        border: 1px solid rgb(200, 200, 200);
        transform: translateY(-10px);
        padding-left: 30px;
    }
    .post--title {
        font-size: 1.7rem;
        font-weight: 700;
        margin-bottom: 0;
    }
    .post--tag {
        display: flex;
        justify-content: center;
        flex-direction: row;
    }
    .tag {
        margin-right: 10px;
        text-decoration: none;
        color: rgb(153, 152, 152);
        font-weight: 700;
        transition: all 0.1s ease-in-out;
    }
    .tag:hover {
        color: rgb(205, 205, 205);
    }
    .date {
        font-size: 0.9rem;
        color: rgb(205, 205, 205);
    }
</style>