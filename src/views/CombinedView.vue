<template>
    <div class="container mt-4">
        <!-- Título centralizado -->
        <h1 class="text-center text-primary mb-4">Lista de Tareas</h1>

        <!-- Input para añadir nuevas tareas -->
        <div class="input-group mb-3">
            <input v-model="newTask" @keyup.enter="addTask" placeholder="Añadir nueva tarea"
                class="form-control task-input" aria-label="Nueva tarea" />
            <button @click="addTask" class="btn btn-primary">Añadir</button>
        </div>

        <!-- Mostrar las tareas obtenidas de la API automáticamente -->
        <div class="row mt-4">
            <div class="col-12 mb-4" v-for="task in tasks" :key="task.id">
                <div class="card mb-3">
                    <div class="card-body d-flex justify-content-between align-items-center">
                        <div class="flex-grow-1 me-2">
                            <h5 class="card-title m-0" :class="{ 'text-decoration-line-through': task.completed }">
                                {{ task.todo }}
                            </h5>
                            <span class="badge"
                                :class="{ 'bg-success': task.completed, 'bg-warning': !task.completed }">
                                {{ task.completed ? 'Completada' : 'Pendiente' }}
                            </span>
                        </div>
                        <div class="d-flex">
                            <button @click="toggleTaskCompletion(task)" class="btn btn-outline-success me-2"
                                aria-label="Marcar como completada">
                                <i :class="task.completed ? 'bi bi-check-circle-fill' : 'bi bi-check-circle'"></i>
                            </button>
                            <button @click="deleteTask(task)" class="btn btn-outline-danger"
                                aria-label="Eliminar tarea">
                                <i class="bi bi-trash"></i>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "CombinedView",
    data() {
        return {
            newTask: "", 
            tasks: [], 
        };
    },
    created() {
        this.fetchTasks();
    },
    methods: {
        fetchTasks() {
            // Obtener las tareas de la API
            axios.get("https://dummyjson.com/todos")
                .then((response) => {
                    this.tasks = response.data.todos; 
                })
                .catch((error) => {
                    console.error("Error fetching tasks:", error);
                });
        },
        addTask() {
            if (this.newTask.trim() === "") return;

            const newTask = {
                todo: this.newTask,
                completed: false,
                id: Date.now(), 
            };

            this.tasks.unshift(newTask);
            this.newTask = ""; 
        },
        toggleTaskCompletion(task) {
            task.completed = !task.completed;
        },
        deleteTask(task) {
            this.tasks = this.tasks.filter((t) => t.id !== task.id);
        },
    },
};
</script>

<style scoped>
.container {
    max-width: 800px;
    padding: 20px;
}

h1 {
    font-size: 50px;
    font-weight: bold;
    font-family: 'Times New Roman', Times, serif;
    text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
}

.task-input {
    border-radius: 25px;
    transition: border-color 0.2s;
}

.task-input:focus {
    outline: none;
    box-shadow: 0 0 5px rgba(0, 123, 255, 0.5);
}

.card-title {
    font-weight: bold;
    overflow-wrap: break-word;
    max-height: 3em;
    overflow: hidden;
}

.text-decoration-line-through {
    text-decoration: line-through;
}
</style>