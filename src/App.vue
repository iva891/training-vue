<script setup lang="ts">
  import { ref } from "vue";

  const users = [
    {id: 1, name: 'Сергей', age: 32},
    {id: 2, name: 'Павел', age: 42},
    {id: 3, name: 'Светлана', age: 27},
    {id: 4, name: 'Ирина', age: 40},
  ];

  const shouldShowList = ref(true);
  const shouldShowOptionalInfo = ref(false);
  const isHovered = ref(false);
</script>

<template>
  <div class="wrapper">
    <button @click="shouldShowList = !shouldShowList" class="button">
      <span v-if="shouldShowList">Скрыть список</span>
      <span v-else>Показать список</span>
    </button>
    <button @click="shouldShowOptionalInfo = !shouldShowOptionalInfo" v-show="shouldShowList" class="button">
      <span v-if="shouldShowOptionalInfo">Скрыть возраст</span>
      <span v-else>Показать возраст</span>
    </button>
    <ul
      v-show="shouldShowList"
      @mouseover="isHovered = true"
      @mouseleave="isHovered = false"
      :class="{ blue: isHovered }"
    >
      <li v-for="user in users" :key="user.id" class="list-item">
        <span>Пользователь {{ user.name }}</span><span v-if="shouldShowOptionalInfo">, возраст {{ user.age }}</span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.button {
  width: fit-content;
  min-width: 200px;
  padding: 8px;

  border-radius: 8px;
  border: solid 1px black;
}

.blue {
  color: blue;
}
</style>
