<template>
    <div class="items">
        <ul v-for="item in items" :key="item.id">
            <li class="item">{{ item.name }} - £{{ item.cost }}
                <button @click="deleteItem(item.id)" class="delete">delete</button>
            </li>
        </ul>
    </div>
</template>

<script setup>

import { ref } from 'vue';
import { defineProps } from 'vue';

const props = defineProps({
    items: Array,
});

const emit = defineEmits(['delete-item']);

const deleteItem = (id) => {
    emit('delete-item', id)
};



</script>

<style scoped>
.items {
    display: flex;
    flex-direction: column;
}

.item {
    display: flex;
    justify-content: space-between;
    min-width: 300px;
}

.item:hover {
    background-color: #f2f2f2;
    scale: 1.01;
    transition: 0.2s ease-in-out;
}

ul {
    list-style: none;
    padding: 0;
    margin: 0;
}

li {
    background-color: #f2f2f2;
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.delete {
    opacity: 0;
    transition: opacity 0.5s;
    background-color: #ff0000;
    color: white;
    border: 0;
    border-radius: 5px;
    cursor: pointer;
    padding: 5px;
    margin-right: 10px;
    margin-left: 50px;

}

li:hover .delete {
    opacity: 1;
}
</style>