<template>
    <div class="bottom-items-container" :class="theme">
        <div class="bottom-items">
            <p class="remaining-todos" :class="mode">5 items left</p>
            <div class="filter-todos-desktop-view" :class="mode">
                <p>All</p>
                <p>Active</p>
                <p>Completed</p>
            </div>
            <p class="clear-todos" :class="mode">Clear Completed</p>
        </div>
    </div>
    <div class="filter-todos-mobile-view" :class="[mode, theme]">
        <div class="actions">
            <p>All</p>
            <p>Active</p>
            <p>Completed</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'TodoSummaryAndFunctionalities',
        props: {
            theme: String,
            mode: String
        }
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
        font-size: 0.8rem;
        justify-content: space-between;
        border-bottom-left-radius: 0.3rem;
        border-bottom-right-radius: 0.3rem;
        width: calc(min(450px, 75vw));
    }

    .bottom-items .remaining-todos.desktop,
    .bottom-items .clear-todos.desktop {
        width: calc(min(135px, 22.5vw));
        /* background-color: red; */
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
        color: var(--very-light-gray);
        background-color: var(--very-dark-desaturated-blue);
    }

    .filter-todos-mobile-view.mobile {
        display: flex;
        justify-content: space-around;
        border-radius: 0.3rem;
        margin-top: 1rem;
        font-size: 1rem;
        font-weight: var(--font-weight-light);
    }

    /* Toggle between showing filtering (all, active and completed)
    in a separate bar or same as the todo list */
    .filter-todos-mobile-view.light {
        color: var(--very-dark-blue);
        background-color: var(--very-light-gray);
    }
    .filter-todos-mobile-view.dark {
        color: var(--very-light-gray);
        background-color: var(--very-dark-desaturated-blue);
    }

    .filter-todos-mobile-view .actions {
        display: flex;
    }

    .filter-todos-mobile-view .actions p {
        font-weight: var(--font-weight-bold);
    }

    .filter-todos-desktop-view.desktop {
        display: flex;
        justify-content: center;
    }

    .filter-todos-desktop-view.mobile {
        display: none;
    }

    .filter-todos-mobile-view.desktop {
        display: none;
    }

    .filter-todos-mobile-view.mobile {
        display: flex;
        justify-content: space-around;
    }
</style>