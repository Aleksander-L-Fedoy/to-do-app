<template>
  <div v-if="!showInput">
    <Button text="Add task" color="black" @click="showInput = true" />
  </div>
  <div v-if="showInput">
    <br />
    <h4>New task</h4>
    <input
      type="text"
      v-model="newTaskTitle"
      placeholder="Write new task here"
    />
    <Button text="Submit" color="navy" @click="addTask()" />
    <Button text="Cancel" color="gray" @click="showInput = false" />
  </div>
  <div v-for="task in sortedTasks" :key="task.id">
    <Task :task="task" />
  </div>
</template>

<script>
import Button from "./Button";
import Task from "./Task.vue";

export default {
  components: { Button, Task },
  props: {
    tasks: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      nextId: 0,
      newTaskTitle: "",
      showInput: false,
    };
  },
  methods: {
    addTask() {
      console.log("addTask method called");
      const newTask = {
        userId: this.userId,
        id: this.nextId++,
        title: this.newTaskTitle,
        completed: false,
      };
      this.tasks.push(newTask);
      this.newTaskTitle = "";
      this.showInput = false;
    },
  },
  computed: {
    sortedTasks() {
      return this.tasks.sort((taskA, taskB) => {
        if (taskA.completed && !taskB.completed) {
          return 1;
        } else if (!taskA.completed && taskB.completed) {
          return -1;
        } else {
          return 0;
        }
      });
    },
  },
};
</script>

<style>
input {
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 8px;
  font-size: 16px;
  width: 100%;
  box-sizing: border-box;
  margin-bottom: 16px;
}

.button-group {
  display: flex;
  justify-content: space-between;
}
</style>
