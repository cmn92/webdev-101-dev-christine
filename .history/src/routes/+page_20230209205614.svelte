<script>
    import {currentUser} from '$lib/pocketbase';

    let caption = '';
</script>
    
{#if $currentUser}
    <div class="flex justify-center">
        <label for="my-model-4" class="btn-primary btn">Create Post</label>

        <input type="checkbox" id="my-model-4" class="modal-toggle" />
        <label for="my-model-4" class="modal cursor-pointer">
            <label class="modal-box relative" for="">
                <h3 class="text-lg font-bold">Create Post</h3>
                <div class="form-control">
                    <label class="label">
                      <span class="label-text">Caption</span>
                    </label>
                    <textarea class="textarea textarea-bordered h-24" placeholder="" bind:value={caption}></textarea>
                    
                  </div>
                  <input type="file" class="file-input file-input-bordered w-full max-w-xs" />
            </label>
        </label>
    </div>
{/if}