<template>
  <div class="container" v-if="usersLength">
    <template v-for="user in users" :key="user.id">
      <div class="users">
        <h2>User name: {{ user.name }}</h2>
        <h3>Age: {{ user.age }}</h3>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: "ActiveUser",
  computed: {
    usersLength() {
      return this.users.length;
    },
  },
  props: {
    users: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.container {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

.users {
  border: 1px solid grey;
}

.users:not(:last-child) {
  margin-bottom: 15px;
}
</style>
