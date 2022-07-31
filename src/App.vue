<template>
  <AppointmentForm />
</template>

<script>
import AppointmentForm from "./components/AppointmentForm.vue";

export default {
  name: "App",
  components: { AppointmentForm },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
