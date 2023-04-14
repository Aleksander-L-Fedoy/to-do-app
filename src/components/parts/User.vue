<template>
  <h2>User {{ userId }}</h2>
  <Tasks :tasks="tasks" />
</template>

<script>
import Tasks from "./Tasks.vue";
import axios from "axios";

export default {
  components: {
    Tasks,
  },
  props: {
    userId: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      tasks: [],
      nextId: 0,
    };
  },
  mounted() {
    this.fetchTasks(this.userId);
  },
  watch: {
    userId: function (newValue) {
      this.fetchTasks(newValue);
    },
  },
  methods: {
    async fetchTasks(userId) {
      try {
        const response = await axios.get(
          `https://jsonplaceholder.typicode.com/users/${userId}/todos`
        );
        this.tasks = response.data;
        this.nextId = this.tasks.length;
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
