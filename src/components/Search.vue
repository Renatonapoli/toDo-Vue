<template>
  <div class="container" :class="{ focused: isFocused }">
    <input type="text" v-model="task" />
    <button @click="setTask">
      Criar <img src="@/assets/addList.svg" alt="Icone de do botão criar" />
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "Search-List",
  emits: ["addTask"],
  props: {
    isFocused: {
      type: Boolean,
      default: false,
    },
  },

  setup(_, { emit }) {
    const task = ref("");

    const setTask = () => {
      emit("addTask", task.value);
      task.value = "";
    };

    return {
      task,
      setTask,
    };
  },
});
</script>

<style scoped>
.container {
  display: flex;
  margin-top: -1.8rem;
  position: relative;
  justify-content: center;

  align-items: center;

  @media (max-width: 768px) {
    flex-direction: column;
    justify-content: start;
    position: inherit;
  }
}

.container input {
  width: 39.875em;
  height: 3.375em;
  background: var(--gray-500);
  border: 1px solid var(--gray-700);
  border-radius: 8px;
  color: var(--gray-100);
  padding: 1rem;

  @media (max-width: 768px) {
    display: flex;
    width: 23.5rem;
    margin-bottom: 1rem;
  }
}
.container input:focus {
  outline: transparent;
  box-shadow: 0 0 0 2px var(--blue-dark);
}

.focused {
  outline: transparent;
  box-shadow: 0 0 0 2px var(--blue-dark);
}

.container button {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: 0.5rem;
  width: 5.625rem;
  height: 3.25rem;
  background: var(--blue-dark);
  color: var(--gray-100);
  font-weight: 700;
  font-size: 0.875rem;
  line-height: 140%;
  gap: 0.5rem;
  border-radius: 0.5rem;
  border: none;
  cursor: pointer;

  transition: 0.8s linear;

  @media (max-width: 768px) {
    width: 4.625rem;
    height: 2.5rem;
    font-size: 0.8rem;
  }
}

.container button:hover {
  background: var(--purple-dark);
  transition-delay: 12ms linear;
}
</style>
