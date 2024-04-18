<template>
    <Header />
    <div class="container">
        <TotalCost :total="+total" />
        <Items :items="items" @delete-item="deleteItem" />
        <AddItem @add-item="addItem" />
    </div>
</template>

<script setup>

import Header from '../components/Header.vue'
import TotalCost from '../components/TotalCost.vue'
import Items from '../components/Items.vue'
import AddItem from '../components/AddItem.vue'
import { ref, computed, onMounted } from 'vue';

onMounted(() => {
    const itemsFromLocalStorage = localStorage.getItem('items');
    if (itemsFromLocalStorage) {
        items.value = JSON.parse(itemsFromLocalStorage);
    }
});

const items = ref([
    { name: 'Cake', cost: 390, isComplete: true, id: 1 },
    { name: 'Flowers', cost: 1200, isComplete: false, id: 2 },
]);

const total = computed(() => {
    return items.value.reduce((acc, item) => acc + item.cost, 0).toFixed(2);
});

const addItem = (newItem) => {
    items.value.push({ ...newItem, id: generateRandomId() });
    saveToLocalStorage();
};

const deleteItem = (id) => {
    items.value = items.value.filter((item) => item.id !== id);
    console.log(items)
    saveToLocalStorage();
};

const generateRandomId = () => {
    return Math.floor(Math.random() * 1000000);
};

const saveToLocalStorage = () => {
    localStorage.setItem('items', JSON.stringify(items.value));
};

</script>

<style></style>