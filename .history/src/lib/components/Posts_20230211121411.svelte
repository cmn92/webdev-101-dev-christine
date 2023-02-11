<script>
	import { onMount } from "svelte";
    import { pb } from "$lib/pocketbase";

    let posts = [];

    onMount(async () => {
       // fetch a paginated records list
    const resultList = await pb.collection('posts').getList(1, 50, {
        sort: '-created',
        expand: 'user',
    });
    posts = resultList.items
});

    
</script>

{#each posts as post (post.id)}
        <div class="card">
            <div class="card-body">
                <p class="card-title">{post.expand.user.username}</p>
                <img src={pb.getFileUrl(post, post.photo)}/>
                <p>{post.caption}</p>
                <p class="card-subtitle">{post.created}</p>
                
            </div>
        </div>
    {/each}