<template>
    <div class="container">
        <h1>TODO App</h1>
        <form @submit.prevent="addTasks" class="task-form">
            <input
                v-model="newTask"
                placeholder="New task"
                class="input-task"
            />
            <button type="submit" class="btn-add">Add</button>
        </form>
        <ul class="task-list">
            <li v-for="task in tasks" :key="task.id" class="task-item">
                <input
                    type="checkbox"
                    v-model="task.completed"
                    @change="updateTask(task)"
                />
                <input
                    v-model="task.title"
                    @blur="updateTask(task)"
                    class="task-title"
                />
                <button @click="deleteTask(task.id)" class="btn-delete">
                    Delete
                </button>
            </li>
        </ul>
    </div>
</template>

<script>
import axios from "axios";

export default {
    data() {
        return {
            tasks: [],
            newTask: "",
        };
    },

    mounted() {
        this.loadTasks();
    },

    methods: {
        async loadTasks() {
            try {
                const res = await axios.get("/api/tasks");
                console.log("Loaded tasks:", res.data.data);
                this.tasks = res.data.data;
            } catch (error) {
                console.error("Failed to load tasks:", error);
            }
        },

        async addTasks() {
            const res = await axios.post("/api/tasks", { title: this.newTask });
            this.tasks.push(res.data.data);
            this.newTask = "";
        },

        async updateTask(task) {
            await axios.put(`/api/tasks/${task.id}`, task);
        },

        async deleteTask(id) {
            await axios.delete(`/api/tasks/${id}`);
            this.tasks = this.tasks.filter((task) => task.id !== id);
        },
    },
};
</script>
