<template>
    <div class="container">
        <div class="todo" :class="theme">
            <TodoHeader :theme="theme"/>
            <TodoSearchBar :theme="theme"/>
            <div class="main-body" :class="[theme, mode]">
                <TodoList
                    :theme="theme"
                    :mode="mode"
                    :todoTasks="this.todoTasks"
                    @mark-completed="onCompleted"
                    @delete-task="onDelete"/>
                <TodoSummaryAndFunctionalities :theme="theme" :mode="mode" :remainingItems="this.remainingItems"/>
            </div>
            <FilterTodosMobileView :theme="theme" :mode="mode" />
        </div>
    </div>
</template>

<script>
    import TodoHeader from './TodoHeader.vue';
    import TodoSearchBar from './TodoSearchBar.vue';
    import TodoList from './TodoList.vue';
    import TodoSummaryAndFunctionalities from './TodoSummaryAndFunctionalities.vue';
    import FilterTodosMobileView from './FilterTodosMobileView.vue';

    export default {
        name: 'ToDo',
        components: {
    TodoHeader,
    TodoSearchBar,
    TodoList,
    TodoSummaryAndFunctionalities,
    FilterTodosMobileView
},
        props: {
            theme: String,
            mode: String
        },
        methods: {
        onCompleted: function (todoTask) {
            this.todoTasks = this.todoTasks.map(task => {
                if (task.id == todoTask.id) {
                    const newStatus = task.status == "active" ? "completed" : "active"
                    task.status = newStatus
                }
                return task;
            })
            this.remainingItems = this.getNoOfActiveTodoTasks()
            console.log(this.remainingItems)
        },
        onDelete: function (deletedTask) {
            this.todoTasks = this.todoTasks.filter(task => {
                return deletedTask.id != task.id
            })
        },
        getNoOfActiveTodoTasks: function () {
            const activeTodos = this.todoTasks.reduce((acc, task) => {
                if (task.status == "active") {
                    acc += 1
                    return acc;
                } else {
                    return acc;
                }
            }, 0)

            return activeTodos;
        }
        },
        data(){
            return {
                todoTasks: [
                    { id: 1, name: "Complete online javascript course", status: "completed" },
                    { id: 2, name: "Jog around the park 3x", status: "active" },
                    { id: 3, name: "10 minutes meditation", status: "active" },
                    { id: 4, name: "Read for 1 hour", status: "active" },
                    { id: 5, name: "Pick up groceries", status: "active" },
                    { id: 6, name: "Complete Todo App on Frontend Mentor", status: "active" }
                ],
                remainingItems: 0
            }
        },
        created(){
            this.remainingItems = this.getNoOfActiveTodoTasks()
        }
    }
</script>

<style scoped>
.container {
        position: absolute;
        left: 0;
        top: 0;
        height: 100vh;
        width: 100vw;
        z-index: 2;
        display: grid;
        place-items: center;
    }

    .container .todo {
        margin: auto;
        height: 90vh;
        width: calc(min(480px, 80vw));
        font-family: var(--primary-font-family);
        font-size: var(--primary-font-size);
        font-weight: var(--font-weight-bold);
    }

    .main-body.light {
        box-shadow: 0 0 1rem -0.5rem var(--very-dark-grayish-blue);
    }
</style>