<template>
  <main>
    <header>
      <img src="./assets/pinia-logo.svg" alt="pinia logo">
      <h1>Pinia Tasks</h1>
    </header>

    <nav class="filter">
      <button @click="filter = 'all'">All task</button>
      <button @click="filter = 'favs'">Fav task</button>
    </nav>

    <div class="task-list" v-if="filter === 'all'">
      <p>all tasks {{ taskStore.totalCount }} tasks left to do </p>
      <div v-for="task in taskStore.tasks" :key="task.id">
        <TaskDetails :task="task" />
      </div>
    </div>
    <div class="task-list" v-if="filter === 'favs'">
      <p>fav tasks {{ taskStore.favCount }} favs left to do</p>
      <div v-for="task in taskStore.favs" :key="task.id">
        <TaskDetails :task="task"/>
      </div>
    </div>
  </main>
</template>

<script>
import { useTaskStore } from './stores/TaskStore';
import { ref } from 'vue';
import TaskDetails from './components/TaskDetails.vue';
export default {
    components: {
      TaskDetails
    },
    setup() {
      const taskStore = useTaskStore();
      const filter = ref('all');
      return { taskStore , filter };
    }
  }
</script>
