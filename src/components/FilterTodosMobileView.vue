<template>
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
        name: 'FilterTodosMobileView',
        props: {
            mode: String,
            theme: String
        }
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
</style>