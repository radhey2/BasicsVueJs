<template>
  <div>
    <h2>Hello {{name}} {{ heroname }}</h2>
  </div>
</template>

<script>
export default {
  name: "Greet_Page",
  props: [
    'name',
    'heroname'
  ],
 
};
</script>

<style scoped></style>
