<template>
  <section>
    <div class="wrapper">
      <UserData @addUser="handleAddUser" />
      <ActiveUser :users="users" />
    </div>
  </section>
</template>

<script>
import UserData from "@/components/User/UserData.vue";
import ActiveUser from "@/components/User/ActiveUser.vue";

export default {
  name: "App",
  components: { UserData, ActiveUser },
  data() {
    return {
      users: [],
    };
  },
  methods: {
    handleAddUser(newUser) {
      this.users.push(newUser);
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.wrapper {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
  border-radius: 6px;
}

button:hover,
button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>
