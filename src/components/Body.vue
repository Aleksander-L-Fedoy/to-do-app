<template>
  <h1>To do app</h1>
  <div class="selectUser">
    <h3>Select user:</h3>
    <select v-model="selectedUserId">
      <option v-for="user in users" :key="user.id" :value="user.id">
        {{ user.id }}
      </option>
    </select>
  </div>
  <User :userId="selectedUserId" />
</template>

<script>
import User from "./parts/User";
import axios from "axios";

export default {
  name: "Body",
  components: { User },
  data() {
    return {
      selectedUserId: 1,
      users: [],
    };
  },
  mounted() {
    this.fetchUsers();
  },
  methods: {
    async fetchUsers() {
      try {
        const response = await axios.get(
          `https://jsonplaceholder.typicode.com/users`
        );
        this.users = response.data;
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style scoped>
select {
  font-size: 1rem;
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
  border: 1px solid #ccc;
  color: #333;
  background-color: #fff;
}

select:hover,
select:focus {
  border-color: #888;
  box-shadow: 0 0 0 2px #eee;
  outline: none;
}
.selectUser {
  float: right;
  padding: 1rem;
}
</style>
