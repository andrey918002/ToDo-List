<script>
   import TaskItem from './TaskItem.svelte'
   let newTask
   let tasks = []

   const addTask = () => {
      if(newTask) {
         tasks = [...tasks, newTask]
         newTask = ''
      }
   }

   const handleKeyEnter = (e) => {
      e.code === 'Enter' && addTask()
      e.code === 'Enter' && renameTask()
   }

   const removeTask = (e) => {
      tasks.splice(e.detail, 1)
      tasks = tasks
   }

   const renameTask = (e) => {
      console.log (e.detail.text)
      tasks.splice(e.detail, 1, e.detail.text)
      tasks = tasks

   }
</script>

<div class="container py-5 h-100">
   <div class="row d-flex justify-content-center align-items-center h-100">
   <div class="col col-xl-10">

      <div class="card" style="border-radius: 15px;">
         <div class="card-body p-5">

         <h6 class="mb-3">Awesome Todo List</h6>
         
         <div class="d-flex justify-content-center align-items-center mb-4">
         <!-- <form class="d-flex justify-content-center align-items-center mb-4"> -->
            <div class="form-outline flex-fill">
               <input on:keydown="{handleKeyEnter}" bind:value={newTask} type="text" id="form3" class="form-control form-control-lg" placeholder="What do you need to do today?"/>
            </div>
            <button on:click={addTask} class="btn btn-primary btn-lg ms-2">Add</button>
         <!-- </form> -->
         </div>

         <ul class="list-group mb-0">
            
               {#each tasks as task, index}
                  <TaskItem on:rename={renameTask} on:remove={removeTask} on:keyEnter={handleKeyEnter} task={task} index={index}/>
               {/each}

         </ul>

         </div>
      </div>

   </div>
   </div>
</div>