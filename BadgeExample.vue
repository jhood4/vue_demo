<template>
  <span> I am a Badge </span>
  <Badge :value="data" severity="danger" />
</template>

<script setup>
import { defineProps } from 'vue';
defineProps({
  data: String,
});
</script>
