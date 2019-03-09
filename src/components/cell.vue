<template>
  <div :class="[$style.cell, {[$style.active]: active}]" @click="editCell()" :style="styles">
    <template v-if="values">{{ values[index] }}</template>
    <template v-else>{{ index + 1}}</template>
  </div>
</template>

<script>
import { eventBus } from "../main.js";

export default {
  created() {
    eventBus.$on("changeProp", data => {
      if (this.active) {
        this.styles.order = data.order;
        this.styles.backgroundColor = data.backgroundColor;
        this.styles.color = data.color;
      }
    });
    eventBus.$on("disableCells", () => {
      this.active = false;
    });
  },
  props: {
    index: Number,
    values: Array
  },
  methods: {
    editCell() {
      eventBus.$emit("disableCells");
      this.active = true;
      eventBus.$emit("editCell", this);
    }
  },
  data() {
    return {
      styles: {
        order: null,
        backgroundColor: null,
        color: null
      },
      active: false
    };
  }
};
</script>

<style lang="sass" module>
	.cell
		/* Display & Box Sizing */
		display: flex
		justify-content: center
		align-items: center
		width: 100px
		height: 100px

		/* Text */
		font-weight: bold
		font-size: 28px

		/* Shadow aka Border */
		box-shadow: 0 0 0 1px #000 inset

		/* Other */
		cursor: pointer
		transition: font-size 0.2s

		&:hover
			/* Text */
			font-size: 36px

	.active
		/* Shadow aka Border */
		box-shadow: 0 0 0 5px #4169e1 inset

		/* Text */
		font-size: 36px
</style>
