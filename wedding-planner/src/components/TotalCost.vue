<template>
    <div class="total-cost">
        <h2>Total Cost</h2>
        <p>£{{ total }}</p>
    </div>
</template>

<script setup>

import { ref, defineProps } from 'vue';

const props = defineProps({
    total: Number,
});

</script>

<style scoped>
.total-cost {

    padding: px;
    margin-bottom: 2rem;
    border-bottom: 1px solid #410a87;
    padding-bottom: 1rem;
}

h2 {

    padding: 10px;
    margin: 0;
    border-radius: 5px 5px 0 0;
}

p {
    padding: 0 10px 0 10px;
    margin: 0;
    border-radius: 0 0 5px 5px;
}
</style>