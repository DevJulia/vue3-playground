<script setup lang="ts">
import { ref, computed } from "vue";

interface Todo {
  name: string;
  completed: boolean;
}

const todos: Todo[] = ref([{ id: 0, name: "Add a task", completed: false }]);
const newTask = ref("");

function addTask() {
  todos.value.unshift({
    id: todos.value.length,
    name: newTask.value,
    completed: false,
  });
  newTask.value = "";
}

function removeTask(taskId) {
  todos.value = todos.value.filter((item) => item.id !== taskId);
}

function dragStart(which, ev) {
  ev.dataTransfer.dropEffect = "move";
  ev.dataTransfer.effectAllowed = "move";
  ev.dataTransfer.setData("itemID", which);
}

function dragFinish(to, ev) {
  const itemID = ev.dataTransfer.getData("itemID");
  moveItem(itemID, to);
}

function moveItem(from, to) {
  todos.value.splice(to, 0, todos.value.splice(from, 1)[0]);
}

const view: ["all", "pending", "completed"] = ref("all");

const filters = {
  all: function (todos) {
    return todos;
  },
  pending: function (todos) {
    return todos.filter(function (todo) {
      return !todo.completed;
    });
  },
  completed: function (todos) {
    return todos.filter(function (todo) {
      return todo.completed;
    });
  },
};

const filteredTodos = computed(() => {
  return filters[view.value](todos.value);
});

function clearTasks() {
  todos.value = todos.value.filter((task) => !task.completed);
}
</script>

<template>
  <main>
    <h2>Todo</h2>
    <form @submit.prevent="addTask">
      <input
        v-model="newTask"
        type="text"
        placeholder="What do you have to do?"
        required
      /><button type="submit">Add</button>
    </form>
    <div class="todo-filters">
      <button @click="view = 'all'">All</button>
      <button @click="view = 'pending'">Pending</button>
      <button @click="view = 'completed'">Completed</button>
    </div>
    <div>
      <button @click="clearTasks">Clear completed</button>
    </div>
    <ul class="todo-list">
      <li
        v-for="(task, idx) in filteredTodos"
        :key="task.id"
        class="list__item"
        draggable="true"
        @dragstart="dragStart(idx, $event)"
        @dragover.prevent
        @drop="dragFinish(idx, $event)"
      >
        <div>
          <input
            class="item__checkbox"
            :id="`task-${task.id}`"
            type="checkbox"
            v-model="task.completed"
          />
          <label class="item__label" :for="`task-${task.id}`">
            {{ task.name }}
          </label>
        </div>
        <button
          class="item__remove"
          title="Remove task"
          @click="removeTask(task.id)"
        >
          <font-awesome-icon :icon="['far', 'trash-alt']" />
        </button>
      </li>
    </ul>
  </main>
</template>

<style scoped lang="scss">
.todo-list {
  list-style-type: none;
  padding: 0;
  max-height: 420px;
  overflow: auto;
}

.list__item {
  display: flex;
  place-content: space-between;
  padding: 0.5rem;
  border: 1px solid var(--color-border);
  margin: 0.5rem 0;

  &:hover {
    border: 1px solid var(--color-border-hover);
  }
}

.item__checkbox {
  margin-right: 1ch;
}
</style>
