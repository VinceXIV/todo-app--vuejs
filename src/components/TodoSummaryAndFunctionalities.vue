<template>
    <div class="bottom-items-container" :class="theme">
        <div class="bottom-items">
            <p class="remaining-todos" :class="mode">{{remainingItems}} items left</p>
            <div class="filter-todos-desktop-view" :class="mode">
                <p :class="currentlyShowing.all" class="all-items" @click="$emit('make-active', 'all')">All</p>
                <p :class="currentlyShowing.active" class="active-items" @click="$emit('make-active', 'active')">Active</p>
                <p :class="currentlyShowing.completed" class="completed-items" @click="$emit('make-active', 'completed')">Completed</p>
            </div>
            <p class="clear-todos" :class="mode" @click="$emit('clear-completed-todos')">Clear Completed</p>
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

    .filter-todos-desktop-view:hover, .clear-todos {
        cursor: pointer;
    }

    .light .filter-todos-desktop-view .active, .dark .filter-todos-desktop-view .active {
        color: var(--bright-blue);
    }

    .light .all-items,
    .light .active-items,
    .light .completed-items,
    .light .clear-todos,
    .light .remaining-todos {
        color: var(--light-grayish-blue);
    }

    .all-items,
    .active-items,
    .completed-items{
        font-weight: 600;
    }

    .light .all-items.inactive:hover,
    .light .active-items.inactive:hover,
    .light .completed-items.inactive:hover,
    .light .clear-todos:hover {
        color: var(--very-dark-blue);
    }

    .dark .all-items.inactive:hover,
    .dark .active-items.inactive:hover,
    .dark .completed-items.inactive:hover,
    .dark .clear-todos:hover {
        color: var(--very-light-gray);
    }
</style>