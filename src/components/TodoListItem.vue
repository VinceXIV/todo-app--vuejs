<template>
    <li :class="theme" class="todo-item item-first">
        <div class="check-mark">
            <div class="circular-div" :class="theme"></div>
        </div>
        <p class="todo-text" :class="theme">{{task.name}}</p>
        <div class="cross">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" :class="mode">
                <path fill="#494C6B" fill-rule="evenodd"
                    d="M16.97 0l.708.707L9.546 8.84l8.132 8.132-.707.707-8.132-8.132-8.132 8.132L0 16.97l8.132-8.132L0 .707.707 0 8.84 8.132 16.971 0z" />
            </svg>
        </div>
    </li>
</template>

<script>
    export default {
        name: 'TodoListItem',
        props: {
            theme: String,
            mode: String,
            task: Object
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

    .todo-item {
        display: flex;
        align-items: center;
    }

    .todo-text {
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
        border: 0.1rem var(--very-dark-grayish-blue) solid;
        border-radius: 100%;
        padding: 0.4rem;
    }

    .check-mark {
        display: grid;
        place-items: center;
        width: calc(min(60px, 10vw));
        height: 2.6rem;
    }

    .cross {
        display: grid;
        place-items: center;
        width: calc(min(60px, 10vw));
        height: 2.6rem;
    }

    .item-first {
        border-top-left-radius: 0.3rem;
        border-top-right-radius: 0.3rem;

    }

    .item-other {
        border-top: 0.005rem solid var(--very-dark-grayish-blue);
    }

    .item-other {
        border-top: 0.005rem solid var(--very-dark-grayish-blue);
    }

    ul li {
        list-style: none;
    }

    .display-none {
        display: none;
    }

    .mobile {
        display: block;
    }

    .desktop {
        display: none;
    }
</style>