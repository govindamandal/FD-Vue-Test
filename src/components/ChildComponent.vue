<template>
    <ul v-if="children.length">

    </ul>
</template>

<script setup>

import { defineProps } from 'vue';

const props = defineProps({
  children: {
    type: Array,
    default: () => []
  }
});

</script>