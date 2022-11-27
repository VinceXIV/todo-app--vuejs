<template>
    <li :class="[theme, `item-${task.id ==1? 'first' : 'not-first'}`]" class="todo-item">
        <div class="check-mark">
            <div class="circular-div" :class="[theme, task.status]">
                <svg xmlns="http://www.w3.org/2000/svg" width="11" height="9" :class="task.status">
                    <path fill="none" stroke="#FFF" stroke-width="2" d="M1 4.304L3.696 7l6-6" />
                </svg>
            </div>
        </div>
        <p class="todo-text" :class="[theme, task.status]">{{task.name}}</p>
        <div class="cross">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" :class="[mode, task.status]">
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

    .todo-item:hover {
        cursor: pointer;
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
        border-radius: 50%;
        width: 1rem;
        height: 1rem;
        /* padding: 0.4rem; */
        display: grid;
        place-items: center;
    }

    .circular-div.completed {
        background: var(--check-background);
    }

    .check-mark {
        display: grid;
        place-items: center;
        width: calc(min(60px, 10vw));
        height: 2.6rem;
    }

    .check-mark svg.completed, .cross svg.completed {
        display: block;
    }

    .check-mark svg.active, .cross svg.active {
        display: none;
    }

    .circular-div:hover{
        border-color: var(--check-background);
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

    .item-not-first {
        border-top: 0.005rem solid var(--very-dark-grayish-blue);
    }

    ul li {
        list-style: none;
    }

    .mobile {
        display: block;
    }

    .desktop {
        display: none;
    }

    .completed {
        text-decoration: line-through;
    }
</style>