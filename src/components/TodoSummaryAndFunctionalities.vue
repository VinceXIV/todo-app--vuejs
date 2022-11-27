<template>
    <div class="bottom-items-container" :class="theme">
        <div class="bottom-items">
            <p class="remaining-todos" :class="mode">{{remainingItems}} items left</p>
            <div class="filter-todos-desktop-view" :class="mode">
                <p :class="currentlyShowing.all" @click="$emit('make-active', 'all')">All</p>
                <p :class="currentlyShowing.active" @click="$emit('make-active', 'active')">Active</p>
                <p :class="currentlyShowing.completed" @click="$emit('make-active', 'completed')">Completed</p>
            </div>
            <p class="clear-todos" :class="mode">Clear Completed</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'TodoSummaryAndFunctionalities',
        props: ["theme", "mode", "remainingItems", "currentlyShowing"]
    }
</script>

<style scoped>
.bottom-items-container {
        display: flex;
        justify-content: space-around;
        border-top: 0.005rem solid var(--very-dark-grayish-blue);
        border-bottom-left-radius: 0.3rem;
        border-bottom-right-radius: 0.3rem;
    }
    .bottom-items {
        display: flex;
        justify-content: space-between;
        border-bottom-left-radius: 0.3rem;
        border-bottom-right-radius: 0.3rem;
        width: calc(min(450px, 75vw));
    }

    .bottom-items .mobile {
        font-size: var(--font-size-set)
    }

    .bottom-items .desktop {
        font-size: var(--font-size-small);
    }

    .bottom-items .remaining-todos.desktop,
    .bottom-items .clear-todos.desktop {
        width: calc(min(135px, 22.5vw));
    }

    p {
        padding-top: 1rem;
        padding-bottom: 1rem;
        padding-left: 0.3rem;
        padding-right: 0.3rem;
    }

    .bottom-items .filter-todos-desktop-view {
        width: calc(min(180px, 30vw));
        flex-direction: row;
    }

    .bottom-items-container.light {
        color: var(--very-dark-blue);
        background-color: var(--very-light-gray);
    }

    .bottom-items-container.dark {
        color: var(--dark-grayish-blue);
        background-color: var(--very-dark-desaturated-blue);
    }

    .filter-todos-desktop-view.desktop {
        display: flex;
        justify-content: center;
    }

    .filter-todos-desktop-view.mobile {
        display: none;
    }

    .remaining-todos:hover, .filter-todos-desktop-view:hover, .clear-todos {
        cursor: pointer;
    }

    .filter-todos-desktop-view .active {
        color: var(--bright-blue)
    }
</style>