<template>
  <div :class="[task.completed ? 'completed' : 'not-completed', 'task']">
    <h3>{{ task.title }}</h3>
    <p>{{ completedText }}</p>
    <Button
      class="button"
      :text="buttonText"
      :color="buttonColor"
      @click="toggleButtonText()"
    />
  </div>
</template>

<script>
import Button from "./Button";
export default {
  props: {
    task: Object,
  },
  components: { Button },
  data() {
    return {
      buttonText: this.task.completed
        ? "Mark task as unfinished"
        : "Mark task as finished",
      buttonColor: this.task.completed ? "gray" : "navy",
      completedText: this.task.completed ? "Completed" : "Not completed",
    };
  },
  methods: {
    toggleButtonText() {
      this.buttonText = this.task.completed
        ? "Mark task as finished"
        : "Mark task as unfinished";
      this.buttonColor = this.task.completed ? "navy" : "grey";
      this.task.completed = !this.task.completed;
      this.completedText = this.task.completed ? "Completed" : "Not completed";
      console.log(this.completed);
      console.log(this.task.completed);
    },
  },
};
</script>

<style>
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.completed {
  border-left: 5px solid darkgray;
}
.task.not-completed {
  border-left: 5px solid navy;
}
</style>
