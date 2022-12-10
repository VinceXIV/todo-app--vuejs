<template>
    <div class="filter-todos-mobile-view" :class="[mode, theme]">
        <div class="actions">
            <p :class="currentlyShowing.all" class="all-items" @click="$emit('make-active', 'all')">All</p>
            <p :class="currentlyShowing.active" class="active-items" @click="$emit('make-active', 'active')">Active</p>
            <p :class="currentlyShowing.completed" class="completed-items" @click="$emit('make-active', 'completed')">Completed</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'FilterTodosMobileView',
        props: ["mode", "theme", "currentlyShowing"]
    }
</script>

<style scoped>
.filter-todos-mobile-view.desktop {
        display: none;
        /* background-color: red; */
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
    box-shadow: 0 0 1rem -0.5rem var(--very-dark-grayish-blue);
    }

    .filter-todos-mobile-view.dark {
        color: var(--very-light-gray);
        background-color: var(--very-dark-desaturated-blue);
    }

    .filter-todos-mobile-view:hover {
        cursor: pointer;
    }
    
    .filter-todos-mobile-view .actions {
        display: flex;
    }
    
    .filter-todos-mobile-view .actions p {
        font-weight: var(--font-weight-bold);
    }
    
    p {
        padding-top: 1rem;
        padding-bottom: 1rem;
        padding-left: 0.3rem;
        padding-right: 0.3rem;
    }

    .filter-todos-mobile-view .active {
        color: var(--bright-blue);
    }

    /* // */
    .light .all-items,
    .light .active-items,
    .light .completed-items,
    .light .clear-todos,
    .light .remaining-todos {
        color: var(--light-grayish-blue);
    }
    
    .light .all-items.inactive:hover,
    .light .active-items.inactive:hover,
    .light .completed-items.inactive:hover,
    .light .clear-todos:hover {
        color: var(--very-dark-blue);
    }

    .dark .all-items.inactive,
    .dark .active-items.inactive,
    .dark .completed-items.inactive,
    .dark .clear-todos {
        color: var(--dark-grayish-blue);
    }

    .dark .all-items.inactive:hover,
    .dark .active-items.inactive:hover,
    .dark .completed-items.inactive:hover,
    .dark .clear-todos:hover {
        color: var(--very-light-gray);
    }

    .light .filter-todos-mobile-view .active,
    .dark .filter-todos-mobile-view .active {
        color: var(--bright-blue);
    }
</style>