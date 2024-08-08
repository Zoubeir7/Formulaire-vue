<template>
  <Formulaire/>
</template>

<script>
import Formulaire from './components/Formulaire.vue';

export default {
  name: 'App',
  components: {
    Formulaire
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  margin: 0;
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 90vh;
}
</style>
