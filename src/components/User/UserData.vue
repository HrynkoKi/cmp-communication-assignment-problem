<template>
  <form @submit.prevent>
    <span v-if="messageError" class="message-error">{{ messageError }}</span>

    <div>
      <label>User name</label>
      <input type="text" v-model.trim="form.name" />
    </div>
    <div>
      <label>Age</label>
      <input type="text" v-model.number="form.age" />
    </div>
    <button type="submit" @click="addUser">Add</button>
  </form>
</template>

<script>
export default {
  name: "UserData",
  data() {
    return {
      form: {
        name: "",
        age: "",
      },
      messageError: "",
    };
  },
  methods: {
    addUser() {
      const { name, age } = this.form;
      const id = Math.random();

      const resultValidation = this.formValidation(name, age);

      if (resultValidation) return;

      const newUser = {
        id,
        name,
        age,
      };

      this.$emit("addUser", newUser);
      this.clearFields();
    },
    formValidation(...details) {
      const [name, age] = details;

      if (!name && !age) {
        this.messageError = "The fields are required fill!";

        return true;
      }

      return false;
    },
    clearFields() {
      this.form.name = "";
      this.form.age = "";
      this.messageError = "";
    },
  },
};
</script>

<style scoped>
input {
  font: inherit;
  padding: 0.15rem;
}
label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
form div {
  margin: 1rem 0;
}

.message-error {
  font-size: 26px;
  font-weight: 700;
  color: #bd0e0e;
}
</style>
