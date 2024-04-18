<template>
    <div class="add-item">
        <input type="text" v-model="name" placeholder="Item name" />
        <input type="number" v-model="cost" placeholder="Item cost" />
        <button @click="addItem">Add Item</button>
    </div>
</template>

<script setup>

import { ref } from 'vue';

const emit = defineEmits(['add-item']);

const name = ref('');
const cost = ref('');

const addItem = () => {

    if (!name.value || !cost.value) {
        name.value = '';
        cost.value = '';
        return;
    }

    const newItem = {
        name: name.value,
        cost: Number(cost.value),
    };


    emit('add-item', newItem);
    name.value = '';
    cost.value = '';
};



</script>

<style scoped>
.add-item {
    display: flex;
    flex-direction: column;
    margin-bottom: 2rem;
}

input {
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
}

button {
    padding: 10px;
    background-color: #56087c;
    color: white;
    border: 0;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #7d3eb7;
}
</style>