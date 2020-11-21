<script>
  //API post 배열을 받아와서 테플릿에 뿌려주는 페이지 axios: API 호출을 용이하게 해주는 javascript node package
  import axios from "axios";
  import { onMount } from "svelte";
  import { Link } from "svelte-routing";
  //axios.get();
  //axios.post();
  let posts;

  onMount(async () => {
    const res = await axios.get("http://blog-api.neulhan.com/posts");
    posts = res.data;
  });
</script>

<h1>List</h1>
{#if posts}
  {#each posts as post}
    <p>
      <Link to="/detail/{post.id}">{post.title}</Link>
    </p>
  {/each}
{:else}
  <p>로딩중..</p>
{/if}
