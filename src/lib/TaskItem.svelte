<script>
   import { createEventDispatcher } from "svelte";

   const dispatch = createEventDispatcher()

   const removeTask = () => {
      dispatch('remove', index)
   }

   const renameTask = () => {
      dispatch('rename', index)
   }

   const handleKeyEnter = () => {
      dispatch('keyEnter', index)
   }

   let checked = false
   export let task
   export let index

</script>
<li class="list-group-item d-flex justify-content-between align-items-center border-start-0 border-top-0 border-end-0 border-bottom rounded-0 mb-1 p-0 pb-2">
   <div class="d-flex align-items-center">
      <input class="form-check-input me-2 p-2" type="checkbox" value="" aria-label="..." bind:checked={checked}/>

      {#if !checked}

      <span class="text-wrap text-break">{task}</span>

      {:else}

      <span class="text-wrap text-break">
         <s>{task}</s>
      </span>

      {/if}

   </div>
   <div class="d-flex btn-group-sm">
      <button class="btn btn-info mx-1" data-bs-toggle="modal" data-bs-target="#editTaskForm{index}">Edit</button>
      <button on:click="{removeTask}" type="button" class="btn btn-danger ml-1">Delete</button>
   </div>
</li>

<div id="editTaskForm{index}" class="modal fade" tabindex="-1" aria-labelledby="editTaskFormLabel" aria-hidden="true">
   <div class="modal-dialog">
      <div class="modal-content">
         <div class="modal-header">
            <h5 class="modal-title" id="editTaskFormLabel">Edit Form</h5>
            <button class="btn-close" data-bs-dismiss="modal" aria-label="close"></button>
         </div>
         <div class="modal-body">
            <input type="text" on:keydown="{handleKeyEnter}" bind:value={task} id="form3 edit-form-input" class="form-control form-control-lg" placeholder="What do you need to do today?">
            
         </div>
         <div class="modal-footer">
            <button class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button on:click="{renameTask}" class="btn btn-secondary">Save</button>
         </div>
      </div>
   </div>
</div>