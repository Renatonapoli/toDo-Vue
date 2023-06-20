<template>
  <div class="containerLists">
    <Search :isFocused="isSearchFocused" @addTask="handleAddTask" />
    <header>
      <div class="taskCreated">
        <p>Tarefas criadas</p>
        <span>{{ tasks.length }}</span>
      </div>
      <div class="completed">
        <p>Concluídas</p>
        <span> {{ completedTasks.length }} de {{ tasks.length }} </span>
      </div>
    </header>

    <section v-for="task in tasks" :key="task.id">
      <ul :class="{ completedTask: task.completed }">
        <input
          type="radio"
          :id="'taskRadio-' + task.id"
          class="radio"
          :checked="task.completed"
          @click="handleTaskClick(task)"
        />
        <p>{{ task.name }}</p>
        <img
          @click="handleDeleteTask(task.id)"
          src="@/assets/trash.svg"
          alt=""
        />
      </ul>
    </section>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

import Search from "../components/Search.vue";

interface Task {
  id: number;
  name: string;
  completed: boolean;
}

export default defineComponent({
  name: "Listas-de-tarefas",
  components: { Search },
  setup() {
    const tasks = ref<Array<Task>>([]);
    const completedTasks = ref<Array<Task>>([]);
    const isSearchFocused = ref<boolean>(false);

    const handleAddTask = (newTask: string) => {
      if (newTask.trim() !== "") {
        tasks.value.push({
          id: tasks.value.length + 1,
          name: newTask,
          completed: false,
        });
        isSearchFocused.value = false;
      }
    };

    const handleDeleteTask = (taskId: number) => {
      const taskIndex = tasks.value.findIndex((task) => task.id === taskId);
      if (taskIndex !== -1) {
        const task = tasks.value[taskIndex];
        tasks.value.splice(taskIndex, 1);
        if (task.completed) {
          completedTasks.value.splice(completedTasks.value.indexOf(task), 1);
        }
      }
    };

    const handleTaskClick = (task: {
      id: number;
      name: string;
      completed: boolean;
    }) => {
      task.completed = !task.completed;
      if (task.completed) {
        completedTasks.value.push(task);
      } else {
        completedTasks.value = completedTasks.value.filter(
          (completedTask) => completedTask.id !== task.id
        );
      }
    };

    return {
      tasks,
      completedTasks,
      handleAddTask,
      handleDeleteTask,
      handleTaskClick,
    };
  },
});
</script>

<style scoped>
.containerLists header {
  display: flex;
  justify-content: space-between;
  margin-top: 4rem;
  margin-bottom: 1.5rem;
}

.taskCreated {
  display: flex;
  margin: 0.5rem;
}

.taskCreated p {
  font-weight: 700;
  margin-left: -0.5rem;
  font-size: 0.88rem;
  color: var(--blue);
}

.taskCreated span {
  display: flex;
  margin-left: 0.5rem;
  justify-content: center;
  background: var(--gray-400);
  width: 1.5rem;
  height: 1.2rem;
  padding: 0.13rem 0.5rem;
  border-radius: 999px;
  gap: 0.8rem;

  font-size: 0.75rem;
  font-weight: 700;
}

.completed {
  display: flex;
  align-items: center;
}

.completed p {
  font-size: 0.75rem;
  font-weight: 700;
  color: var(--purple);
}

.completed span {
  display: flex;
  margin-left: 0.5rem;
  justify-content: center;
  background: var(--gray-400);
  width: 3.75rem;
  height: 1.1875rem;
  padding: 0.13rem 0.5rem;
  border-radius: 999px;
  gap: 0.8rem;

  font-size: 0.75rem;
  font-weight: 700;
}

section {
  white-space: normal;
  background: var(--gray-500);
  width: 46rem;
  height: 72px;
  padding: 1rem;
  margin-bottom: 1rem;
  border: 1px solid var(--gray-400);
  box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.06);
  border-radius: 8px;

  @media (max-width: 768px) {
    width: 24rem;
    height: 3rem;
    padding: 0.5rem;
  }
}

section ul {
  display: flex;
  justify-content: space-between;
}

section input {
  appearance: initial;
  border: 2px solid var(--blue);
  border-radius: 50%;

  width: 1.063rem;
  height: 1.063rem;

  @media (max-width: 768px) {
    width: 2rem;
  }
}

section input:checked {
  border: none;
  background: url(@/assets/check.svg) no-repeat var(--purple-dark);
  background-position: center;
}

section p {
  width: 45rem;

  word-break: break-word;
  margin-right: auto;
  margin-left: 0.75rem;
  margin-bottom: 0.75rem;
  font-size: 0.875rem;

  @media (max-width: 768px) {
    margin-bottom: 1rem;
  }
}

.completedTask {
  text-decoration: line-through;
}

section img {
  width: 1.5rem;
  height: 1.5rem;
}
</style>
