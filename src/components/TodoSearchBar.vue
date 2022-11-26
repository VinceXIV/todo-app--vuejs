<template>
    <form>
        <div id="input-field" :class="theme">
            <div id="circular-div" :class="theme"></div>
            <input type="text" name="new-todo" id="new-todo" :class="theme">
        </div>
    </form>
</template>

<script>
    export default {
        name: 'TodoSearchBar',
        props: ["theme"]
    }
</script>

<style>
    .dark {
        background-color: var(--very-dark-desaturated-blue);
        color: var(--very-light-gray)
    }

    .light {
        background-color: var(--very-light-gray);
        color: var(--very-dark-blue)
    }

    form #input-field {
        display: flex;
        align-items: center;
        border-radius: 0.2rem;
    }

    form input {
        position: relative;
        box-sizing:content-box;
        width: 100%;
        padding: 0.5rem;
        outline: none;
        border: none;
        font-weight: var(--font-weight-light);
        font-size: var(--primary-font-size);
    }

    form #circular-div {
        border: 0.1rem var(--very-dark-grayish-blue) solid;
        border-radius: 100%;
        padding: 0.8rem;
        margin: 1rem;
    }
</style>