<template>
    <div class="container">
        <div class="todo">
            <TodoHeader :theme="theme"/>
            <TodoSearchBar :theme="theme"/>
        </div>
    </div>
</template>

<script>
    import TodoHeader from './TodoHeader.vue';
    import TodoSearchBar from './TodoSearchBar.vue';

    export default {
        name: 'ToDo',
        components: {
            TodoHeader,
            TodoSearchBar
        },
        props: {
            theme: String
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
        /* background-color: red; */
    }
</style>