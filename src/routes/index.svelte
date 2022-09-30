<script context="module">
    const allPosts = import.meta.glob("./blogs/*.{md,svx}");

    let body = [];
    for (let path in allPosts) {
        body.push(
        allPosts[path]().then(({ metadata }) => {
            return { path, metadata };
        })
        );
    }
    export const load = async () => {
        const posts = await Promise.all(body);

        return {
        props: {
            posts,
        },
        };
    };
</script>

<script>
    import BlogCard from "$lib/BlogCard.svelte";
    export let posts;

    const dateSortedPosts = posts.slice().sort((post1, post2) => {
        return new Date(post2.metadata.date) - new Date(post1.metadata.date);
    });
</script>

<div class="container">
    <div class="post--container">
    {#each dateSortedPosts as { path, metadata: { title, tags, date } }}
    <div class="post--content">
        <BlogCard {title} date={new Date(date).toDateString()} {tags} path={path.replace(".md", "").replace(".svx", "")} />
    </div>
    {/each}
    </div>
</div>

<style>
    .container {
        width: 100%;
    }
    .post--container {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr; 
        gap: 40px;
    }
</style>
