<script>
  export let title, intro, blog, source, content, allContent;
  import Gallery from "../components/gallery.svelte";

  function handleClick(e) {
    console.log(e);
  }

  import Grid from "../components/grid.svelte";
  import Uses from "../components/source.svelte";
  import Pager from "../components/pager.svelte";

  $: currentPage = content.pager;
  let postsPerPage = 3;
  let allPosts = allContent.filter((content) => content.type == "blog");
  let totalPosts = allPosts.length;
  let totalPages = Math.ceil(totalPosts / postsPerPage);
  $: postRangeHigh = currentPage * postsPerPage;
  $: postRangeLow = postRangeHigh - postsPerPage;
</script>

<h1>{title}</h1>

<Gallery on:click={handleClick}>
  <img src="https://via.placeholder.com/180x200/1" alt="" />
  <img src="https://via.placeholder.com/200x280/1" alt="" />
  <img src="https://via.placeholder.com/250x200/1" alt="" />
  <img src="https://via.placeholder.com/140x310/1" alt="" />
  <img src="https://via.placeholder.com/280x300/1" alt="" />
  <img src="https://via.placeholder.com/220x100/1" alt="" />
  <img src="https://via.placeholder.com/180x150/1" alt="" />
  <img src="https://via.placeholder.com/210x180/1" alt="" />
  <img src="https://via.placeholder.com/210x200/1" alt="" />
  <img src="https://via.placeholder.com/200x250/1" alt="" />
  <img src="https://via.placeholder.com/220x200/1" alt="" />
  <img src="https://via.placeholder.com/180x240/1" alt="" />
  <img src="https://via.placeholder.com/210x210/1" alt="" />
  <img src="https://via.placeholder.com/200x220/1" alt="" />
  <img src="https://via.placeholder.com/210x200/1" alt="" />
  <img src="https://via.placeholder.com/180x200/1" alt="" />
  <img src="https://via.placeholder.com/200x280/1" alt="" />
  <img src="https://via.placeholder.com/250x200/1" alt="" />
  <img src="https://via.placeholder.com/140x210/1" alt="" />
  <img src="https://via.placeholder.com/280x200/1" alt="" />
  <img src="https://via.placeholder.com/220x100/1" alt="" />
  <img src="https://via.placeholder.com/180x150/1" alt="" />
  <img src="https://via.placeholder.com/210x180/1" alt="" />
  <img src="https://via.placeholder.com/210x200/1" alt="" />
  <img src="https://via.placeholder.com/200x250/1" alt="" />
  <img src="https://via.placeholder.com/220x200/1" alt="" />
  <img src="https://via.placeholder.com/180x240/1" alt="" />
  <img src="https://via.placeholder.com/210x210/1" alt="" />
  <img src="https://via.placeholder.com/200x220/1" alt="" />
  <img src="https://via.placeholder.com/210x200/1" alt="" />
</Gallery>

<section id="intro">
  {#each intro as paragraph}
    <p>{@html paragraph}</p>
  {/each}
</section>

{#if blog}
  <div>
    <h3>Recent blog posts:</h3>
    <Grid items={allPosts} {postRangeLow} {postRangeHigh} />
    <br />
  </div>
  <Pager {currentPage} {totalPages} />
{/if}

{#if source}
  <Uses {content} {source} />
{/if}
