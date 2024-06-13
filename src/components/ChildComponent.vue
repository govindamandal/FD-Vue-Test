<template>
    <ul v-if="items.length">
        <li v-for="(item, index) in items" :key="item.id">
            <label class="container">{{ item.name }}
                <input type="checkbox" :checked="item.checked" @change="onChange($event, index)">
                <span class="checkmark"></span>
                <child-component v-if="item.checked" :children="item.children" />
            </label>
        </li>
    </ul>
</template>

<script setup>

import { defineProps, reactive } from 'vue';

const props = defineProps({
    children: {
        type: Array,
        default: () => []
    }
});

const items = reactive(props.children);

function onChange(evt, index) {
    items[index].checked = evt.target.checked;
}

</script>