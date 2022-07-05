<script>
  import styles from './css/app.module.css'
  import logo from './assets/svelte.png'
  import TaskList from './lib/TaskList.svelte';
</script>

<main>
  <section class="min-vh-100" style="background-color: #c2d2de;">
    <img src={logo} alt="Svelte Logo" />
    <h1>Task List by Svelte!</h1>
    <TaskList/>
  </section>
</main>
