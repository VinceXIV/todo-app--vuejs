<template>
    <div>
        <ul id="todo-list" :class="theme">
            <TodoListItem
                v-for="task in showTasks"
                :key="task.id"
                :task="task"
                :theme="theme"
                :mode="mode"
                @toggle-todo-state="onToggleTodoState"
                @remove-todo-item="onRemoveTodoItem"/>
        </ul>
    </div>
</template>

<script>
    import TodoListItem from './TodoListItem.vue';
    export default {
        name: 'TodoList',
        props: {
            todoTasks: Object,
            theme: String,
            mode: String
        },
        components: {
            TodoListItem
        },
        methods: {
            onToggleTodoState: function(todoTask){
                this.showTasks = this.showTasks.map(task => {
                    if(task.id == todoTask.id){
                        const newStatus = task.status == "active"? "completed" : "active"
                        task.status = newStatus
                    }
                    return task;
                })
            },
            onRemoveTodoItem: function(deletedTask){
                if(deletedTask.status === "completed"){
                    this.showTasks = this.showTasks.filter(task => task.id !== deletedTask.id)
                }
            }
        },
        data() {
            return {
                showTasks: this.todoTasks
            }
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