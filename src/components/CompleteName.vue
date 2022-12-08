<template>
  <div class="completeName">
    <h2>Nome Completo</h2>
    <p>{{name}} {{lastname}}</p>
  </div>
</template>

<script>
export default {
  props: {
    name: "",
    lastname: "",
  },
};
</script>

<style>
.completeName {
  margin-top: .5em;
  margin-bottom: .3em;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
</style>