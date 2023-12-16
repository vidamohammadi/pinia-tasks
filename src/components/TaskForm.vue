<template>
    <form @submit.prevent="handleSubmint">
        <input
            type="text"
            placeholder="I need to..."
            v-model="newTask">
            <button>Add</button>
    </form>
</template>

<script>
import { useTaskStore } from '@/stores/TaskStore';
import { ref } from 'vue';

    export default {
    setup() {
            const taskStore = useTaskStore()
            const newTask = ref('')

            const handleSubmint = () => {
                if (newTask.value.length > 0) {
                    taskStore.addTask({
                        title: newTask.value,
                        isFav: false,
                        id: Math.floor(Math.random() * 10000)
                    })
                    newTask.value = ''
                }
            }
            return {handleSubmint , newTask}
        }
    }
</script>