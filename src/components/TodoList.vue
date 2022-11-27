<template>
    <div>
        <ul id="todo-list" :class="theme">
            <TodoListItem v-for="task in todoTasks" :key="task.id" :task="task" :theme="theme" :mode="mode"/>
        </ul>
    </div>
</template>

<script>
    import TodoListItem from './TodoListItem.vue';
    export default {
        name: 'TodoList',
        props: {
            todoTasks: {
                type: Array,
                default: () => [
                    {id: 1, name: "Complete online javascript course", status: "completed"},
                    {id: 2, name: "Jog around the park 3x", status: "active"},
                    {id: 3, name: "10 minutes meditation", status: "active"},
                    {id: 4, name: "Read for 1 hour", status: "active"},
                    {id: 5, name: "Pick up groceries", status: "active"},
                    {id: 6, name: "Complete Todo App on Frontend Mentor", status: "active"}
                ]
            },
            theme: String,
            mode: String
        },
        components: {
            TodoListItem
        }        
    }
</script>

<style scoped>
.dark {
        background-color: var(--very-dark-desaturated-blue);
        color: var(--very-light-gray)
    }

    .light {
        background-color: var(--very-light-gray);
        color: var(--very-dark-blue)
    }

    #todo-list {
        margin-top: 1rem;
        border-radius: 0.2rem;
    }
</style>