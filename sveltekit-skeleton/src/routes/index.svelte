<script context="module">

  export const load = async ({ fetch }) => {
  
    const res = await fetch(`/posts.json`);

    if(res.ok) {
      
      const posts = await res.json();
      
      return {
        props: 
          posts,
        
      }
    }
  }
</script>

<script>
  export let posts
</script>

<!-- <pre>{JSON.stringify(posts, null, 2)}</pre> -->

{#each posts as {title,
  slug,
  date,
  excerpt,
  tags,
  coverImage,}}
  <li class="card text-center">
    <figure>
      <img src={coverImage.url} alt={title}>
    </figure>
    <p>{title}</p>
    <p>{excerpt}</p>
    <a class="btn" href={`/posts/${slug}`}>Read More</a>
    
  </li>
  
{/each}
