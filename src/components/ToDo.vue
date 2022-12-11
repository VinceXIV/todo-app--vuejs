<template>
    <div class="container">
        <div class="todo" :class="theme">
            <TodoHeader :theme="theme" @toggleTheme="$emit('toggleTheme')"/>
            <TodoNew :theme="theme" @new-todo="onAdd"/>
            <div class="main-body" :class="[theme, mode]">
                <TodoList
                    :theme="theme"
                    :mode="mode"
                    :todoTasks="this.todoTasks"
                    @mark-completed="onCompleted"
                    @delete-task="onDelete"/>
                <TodoSummaryAndFunctionalities
                    :theme="theme"
                    :mode="mode"
                    :remainingItems="this.remainingItems"
                    :currentlyShowing="currentlyShowing"
                    @make-active="onMakeActive"
                    @clear-completed-todos="onClearCompleted"/>
            </div>
            <FilterTodosMobileView
                :theme="theme"
                :mode="mode"
                :currentlyShowing="currentlyShowing"
                @make-active="onMakeActive"/>
        </div>
    </div>
</template>

<script>
    import TodoHeader from './TodoHeader.vue';
    import TodoNew from './TodoNew.vue';
    import TodoList from './TodoList.vue';
    import TodoSummaryAndFunctionalities from './TodoSummaryAndFunctionalities.vue';
    import FilterTodosMobileView from './FilterTodosMobileView.vue';


    export default {
        name: 'ToDo',
        components: {
        TodoHeader,
        TodoNew,
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
                    this.allTodoTasks.find(aTask => aTask.id == task.id).status = newStatus
                    task.status = newStatus
                }
                return task;
            })
            this.remainingItems = this.getNoOfActiveTodoTasks()
        },

        onDelete: function (deletedTask) {
            this.todoTasks = this.todoTasks.filter(task => {
                return deletedTask.id != task.id
            })
            this.allTodoTasks = this.allTodoTasks.filter(task => {
                return deletedTask.id != task.id
            })
        },

        onAdd: function(newTodoName){
            let newTodoId = 0
            if(this.todoTasks.length){
                newTodoId = this.todoTasks.reduce((a, b) => Math.max(a, b.id), -Infinity) + 1
            }
            const newTodoStatus = "active"

            this.todoTasks = [...(this.todoTasks), {id: newTodoId, name: newTodoName, status: newTodoStatus}]
            this.allTodoTasks = [...(this.allTodoTasks), { id: newTodoId, name: newTodoName, status: newTodoStatus }]
            this.remainingItems = this.getNoOfActiveTodoTasks()
        },

        onMakeActive: function(activeItem){
            this.updateColor(activeItem)
            this.updateDisplayedItems(activeItem)
        },

        onClearCompleted: function(){
            this.allTodoTasks = this.allTodoTasks.filter(task => task.status != "completed")
            this.todoTasks = this.todoTasks.filter(task => task.status != "completed")
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
        },

        updateColor: function(activeItem){
            this.currentlyShowing = {
                all: activeItem == "all" ? "active" : "inactive",
                active: activeItem == "active" ? "active" : "inactive",
                completed: activeItem == "completed" ? "active" : "inactive"
            }                
        },

        updateDisplayedItems: function(activeItem){
            if(activeItem == "all"){
                this.todoTasks = this.allTodoTasks
            }else if (activeItem == "active"){
                this.todoTasks = this.allTodoTasks.filter(task => task.status == "active")
            } else if (activeItem == "completed") {
                this.todoTasks = this.allTodoTasks.filter(task => task.status == "completed")
            }
        }
    },


    data(){
        return {
            allTodoTasks: [
                { id: 1, name: "Complete online javascript course", status: "completed" },
                { id: 2, name: "Jog around the park 3x", status: "active" },
                { id: 3, name: "10 minutes meditation", status: "active" },
                { id: 4, name: "Read for 1 hour", status: "active" },
                { id: 5, name: "Pick up groceries", status: "active" },
                { id: 6, name: "Complete Todo App on Frontend Mentor", status: "active" }
            ],   

            todoTasks: [
                { id: 1, name: "Complete online javascript course", status: "completed" },
                { id: 2, name: "Jog around the park 3x", status: "active" },
                { id: 3, name: "10 minutes meditation", status: "active" },
                { id: 4, name: "Read for 1 hour", status: "active" },
                { id: 5, name: "Pick up groceries", status: "active" },
                { id: 6, name: "Complete Todo App on Frontend Mentor", status: "active" }
            ],

            remainingItems: 0,

            currentlyShowing: {
                all: "active",
                active: "inactive",
                completed: "inactive"
            }
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