<template>
    <form  @submit="handleNewTodoSubmit">
        <div id="input-field" :class="theme">
            <div class="check-mark">
                <div class="circular-div" :class="theme"></div>
            </div>
            <input type="text" name="new-todo" id="new-todo" :class="theme">
            <div class="cross-dummy"></div>
        </div>
    </form>
</template>

<script>
    export default {
        name: 'TodoSearchBar',

        props: ["theme"],
        
        methods: {
            handleNewTodoSubmit(e){
                e.preventDefault()
                const formInput = e.target.querySelector('#new-todo') 
                this.$emit('new-todo', formInput.value)
                e.target.reset()
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

    form #input-field {
        display: flex;
        align-items: center;
        border-radius: 0.3rem;
        box-shadow: 0 0 1rem -0.5rem var(--very-dark-grayish-blue);
        caret-color: hsl(192, 100%, 67%);
    }

    form input#new-todo {
        position: relative;
        box-sizing: content-box;
        padding-top: 0.7rem;
        padding-bottom: 0.7rem;
        outline: none;
        border: none;
        font-weight: var(--font-weight-light);
        font-size: var(--font-size-set);
        width: calc(min(360px, 80vw));
    }

    .circular-div {
        border-radius: 100%;
        padding: 0.4rem;
    }

    .circular-div.dark {
        border: 0.1rem var(--very-dark-grayish-blue) solid;
    }

    .circular-div.light {
        border: 0.1rem var(--light-grayish-blue) solid;
    }

    .check-mark {
        display: grid;
        place-items: center;
        width: calc(min(60px, 10vw));
        height: 2.6rem;
    }

    /* There won't be a cross like the todo list */
    /* only doing this to for uniformity with the list */
    .cross-dummy {
        display: grid;
        place-items: center;
        width: calc(min(60px, 10vw));
        height: 2.6rem;
    }
</style>