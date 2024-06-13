<template>
  <div class="container">
    <h1> Recursive parent-children components </h1>
    <ul>
      <li v-for="(parent, index) in parents" :key="index">
        <label class="container">{{ parent.name }}
          <input type="checkbox" :checked="parent.checked">
          <span class="checkmark"></span>
        </label>
        <ul v-if="parent.children">
          <li v-for="(child, key) in parent.children" :key="key">
            {{ child.name }}
            <ul v-if="child.children">
              <li v-for="(subchild, subkey) in child.children" :key="subkey">
                {{ subchild.name }}
              </li>
            </ul>
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>
<script setup>
import { reactive } from 'vue';
import data from './data.js';
const parents = reactive(data);
</script>
