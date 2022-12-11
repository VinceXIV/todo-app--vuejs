<template>
    <div>
        <ul id="todo-list" :class="theme">
            <TodoListItem
                v-for="task in todoTasks"
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
                this.$emit('mark-completed', todoTask)
            },
            onRemoveTodoItem: function(deletedTask){
                if(this.mode == 'mobile'){
                    this.$emit('delete-task', deletedTask)
                }
            }
        },
        emits: ['mark-completed', 'delete-task']    
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
        padding-top: 0.2rem;
    }
</style>