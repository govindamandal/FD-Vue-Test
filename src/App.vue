<template>
  <div class="container">
    <h1> Recursive parent-children components </h1>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <label class="container">{{ item.name }}
          <input type="checkbox" :checked="item.checked" @change="onChange($event, index)">
          <span class="checkmark"></span>
        </label>
        <child-component v-if="item.checked" :children="item.children" />
      </li>
    </ul>
  </div>
</template>
<script setup>

import { reactive } from 'vue';
import ChildComponent from './components/ChildComponent.vue';

import data from './data.js';
const items = reactive(data);

function onChange(evt, index) {
  items[index].checked = evt.target.checked;
}

</script>
