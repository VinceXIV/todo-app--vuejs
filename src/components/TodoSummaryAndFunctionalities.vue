<template>
    <div class="bottom-items-container" :class="theme">
        <div class="bottom-items">
            <p class="remaining-todos">5 items left</p>
            <div class="filter-todos">
                <p>All</p>
                <p>Active</p>
                <p>Completed</p>
            </div>
            <p class="clear-todos">Clear Completed</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'TodoSummaryAndFunctionalities',
        props: {
            theme: String
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

    p {
        padding: 0.7rem;
    }

    .bottom-items .filter-todos {
        display: flex;
    }

    .bottom-items-container.light {
        color: var(--very-dark-blue);
        background-color: var(--very-light-gray);
    }

    .bottom-items-container.dark {
        color: var(--very-light-gray);
        background-color: var(--very-dark-desaturated-blue);
    }
</style>