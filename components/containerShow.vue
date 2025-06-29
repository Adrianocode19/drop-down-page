<template>
  <div class="containerShow" @click="$emit('toggle')">
    <h2 class="topics">{{ title }}</h2>
    <img
      v-if="!isOpen"
      class="iconShow"
      src="../public/assets/icons/colapsed.svg"
      alt="collapsed"
    />
    <img
      v-else
      class="iconShow"
      src="../public/assets/icons/open.svg"
      alt="open"
    />
  </div>
</template>

<script setup>
defineProps({
  isOpen: Boolean,
  title: String,
});

defineEmits(["toggle"]);
</script>

<style scoped>
.containerShow {
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
}
</style>
