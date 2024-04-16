<template>
  <div class="sort-buttons">
    <h3>{{ title }}</h3>
    <div class="sort-options">
      <button
          @click="emitSort('1')"
          :class="{ selected: selectedSortType === '1' }"
          class="sort-asc"
      > По возрастанию
        <img class="icon" src="/up.svg" alt="По возрастанию">
      </button>
      <button
          @click="emitSort('2')"
          :class="{ selected: selectedSortType === '2' }"
          class="sort-desc"
      > По убыванию
        <img class="icon" src="/down.svg" alt="По убыванию">
      </button>
      <button
          @click="emitSort('0')"
          :class="{ selected: selectedSortType === '0' }"
          class="sort-none"
      > Без сортировки
        <img class="icon" src="/none.svg" alt="Без сортировки">
      </button>
    </div>
  </div>
</template>


<script setup>
import { ref, defineEmits } from 'vue';

const props = defineProps({
  title: {
    type: String,
    default: 'Сортировка по рейтингу'
  }
});

const selectedSortType = ref(null);

// Определение событий, которые может отправлять компонент
const emit = defineEmits(['sort']);

const emitSort = (sortType) => {
  selectedSortType.value = sortType;
  emit('sort', sortType);
};

</script>

<style lang="scss" scoped>
.sort-buttons {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  margin-top: 10px;
  font-size: 10pt;
}
.sort-buttons h3 {
  text-align: center;
  width: 100%;
  color: #f0f0f0;
  margin-bottom: 15px;
  font-size: 18pt;
}
.sort-buttons .sort-options {
  display: flex;
  justify-content: space-between;
  width: 100%;
  gap: 10px;
}
.sort-buttons button {
  background: #f0f0f0;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 10%;
}
.sort-buttons button:hover {
  background: #e0e0e0;
}
.sort-buttons button.selected {
  background: rgba(28, 122, 208, 0.46);
  color: white;
  border-radius: 10%;
  box-shadow: 0 0 27px rgba(28, 122, 208, 0.46), 0 0 5px rgba(28, 122, 208, 0.46);
}
.icon {
  width: 16px;
  height: 16px;
  margin-right: 5px;
}
.sort-buttons button.selected .icon {
  filter: invert(1);
}
</style>




