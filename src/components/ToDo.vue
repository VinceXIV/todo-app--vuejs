<template>
    <div class="container">
        <div class="todo"></div>
    </div>
</template>

<script>
    export default {
        name: 'ToDo'
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
        background-color: red;
    }
</style>