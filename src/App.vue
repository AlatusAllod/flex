<template>
  <section class="flex">
    <workfield></workfield>
    <editor></editor>
    <modal></modal>
  </section>
</template>

<script>
import workfield from "./components/workfield";
import editor from "./components/editor";
import modal from "./components/modal";

export default {
  name: "app",
  components: {
    workfield,
    editor,
    modal
  }
};
</script>

<style>
@import "assets/css/normalize.css";
@import "https://fonts.googleapis.com/css?family=Roboto:400,700";

body {
  /* Text */
  font-family: "Roboto", sans-serif;
}

.flex {
  /* Display & Box Sizing */
  display: flex;
}

input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  /* Display & Box Sizing */
  -webkit-appearance: none;
  margin: 0;
}

input:focus {
  /* Display & Box Sizing */
  outline: none;
}
</style>

