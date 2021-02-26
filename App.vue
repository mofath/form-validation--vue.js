<template>
  <form class="form" @submit.prevent="submit">
    <my-input
      name="Username"
      :rules="{ required: true, min: 5 }"
      :value="username.value"
      @update="update"
      type="text"
    />

    <my-input
      name="Password"
      :rules="{ required: true, min: 5 }"
      :value="password.value"
      @update="update"
      type="password"
    />

    <my-button color="white" background="darkslateblue" :disabled="!valid" />
  </form>
</template>



<script>
import MyButton from "./MyButton.vue";
import MyInput from "./MyInput.vue";

export default {
  components: {
    MyButton,
    MyInput,
  },
  data() {
    return {
      username: {
        value: "user",
        valid: false,
      },
      password: {
        value: "",
        valid: false,
      },
    };
  },
  computed: {
    valid() {
      return this.username.valid && this.password.valid;
    },
  },
  methods: {
    update(payload) {
      this[payload.name.toLowerCase()] = {
        value: payload.value,
        valid: payload.valid,
      };
    },
    submit() {
      console.log("submit");
    },
  },
};
</script>



<style scoped>
body {
  font-family: Arial;
}

.form {
  max-width: 400px;
  width: 50%;
}
</style>




