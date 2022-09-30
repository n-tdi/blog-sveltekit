<script context="module">
  const allPosts = import.meta.glob("../blogs/*.{md,svx}");

  let body = [];
  for (let path in allPosts) {
    body.push(
      allPosts[path]().then(({ metadata }) => {
        return { path, metadata };
      })
    );
  }
  export const load = async ({ params }) => {
    const posts = await Promise.all(body);
    const tag = params.tag;

    const filteredPosts = posts.filter((post) => {
      return post.metadata.tags.includes(tag);
    });

    return {
      props: {
        filteredPosts,
        tag,
      },
    };
  };
</script>

<script>
    import BlogCard from "$lib/BlogCard.svelte";
    export let filteredPosts, tag;
</script>

<h1 class="title">#{tag}</h1>

<div class="container">
    <div class="post--container">
    {#each filteredPosts as { path, metadata: { title, tags, date } }}
    <div class="post--content">
        <BlogCard {title} date={new Date(date).toDateString()} {tags} path={path.replace("./tags", "/blogs").replace(".md", "").replace(".svx", "")} />
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
    .title {
        size: 1.5rem;
        display: flex;
        justify-content: center;
        margin-bottom: 10px;
    }
</style>