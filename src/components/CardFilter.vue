<template>
  <select @change="changeOptions" class="container">
    <option disabled selected value="default">Выберите из списка</option>
    <option v-for="option in options" :key="option.value" :value="option.value">
      {{ option.name }}
    </option>
  </select>
</template>

<script setup>
import { ref } from "vue";

const options = ref([
  { value: "default", name: "Сбросить фильтр" },
  { value: "down", name: "По убыванию рейтинга" },
  { value: "up", name: "По возрастанию рейтинга" },
]);

const emit = defineEmits("update");

function changeOptions(event) {
  emit("update", event.target.value);
}
</script>

<!-- compositionAPI но без <script setup> для референса -->

<!-- <script>
import { ref } from "vue";

export default {
  emits: ['update'],
  setup(_, context) {
    const options = ref([
      { value: "default", name: "Сбросить фильтр" },
      { value: "down", name: "По убыванию рейтинга" },
      { value: "up", name: "По возрастанию рейтинга" },
    ]);

    function changeOptions(event) {
      context.emit('update', event.target.value);
    }

    return {
      options,
      changeOptions,
    };
  },
};
</script> -->

<style scoped>
.container {
  background: white;
  padding: 0 13rem 0 0.2rem;
  margin: 0 0 0.5rem 0;
  border-radius: 5px;
}
</style>
