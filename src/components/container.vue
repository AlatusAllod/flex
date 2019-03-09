<template>
  <div :class="$style.container" :style="container.styles">
    <cell
      v-for="(cell, index) in container.cells"
      :index="index"
      :values="container.values"
      :key="cell"
    ></cell>
  </div>
</template>

<script>
import cell from "./cell";
export default {
  components: {
    cell
  },
  props: {
    container: Object
  }
};
</script>

<style lang="sass" module>
	.container
		/* Display & Box Sizing */
		display: flex
		flex-wrap: wrap

		/* Shadow aka Border */
		box-shadow: 0 0 0 2px #000 inset
</style>
