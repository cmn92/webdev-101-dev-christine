<script>
	import { onMount } from "svelte";
    import { pb } from "$lib/pocketbase";

    let posts = [];

    onMount(async () => {
       // fetch a paginated records list
    const resultList = await pb.collection('posts').getList(1, 50, {
        filter: 'created >= "2022-01-01 00:00:00" && someFiled1 != someField2',
    });
    posts = resultList.items
});

    
</script>

{#each posts as post (post.id)}
        <div class="card">
            <div class="card-body">
                <h2 class="card-title">{post.caption}</h2>
                <p class="card-subtitle">{post.created}</p>
                <p class="card-text">{post.user}</p>
            </div>
        </div>
    {/each}