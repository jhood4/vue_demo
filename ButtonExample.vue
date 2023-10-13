<template>
  <div>
    I am a Button
  </div>
  <Button :label="data" severity="success" />
</template>

<script setup>
import { defineProps } from 'vue';
defineProps({
  data: String,
});
</script>
