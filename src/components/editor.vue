<template>
  <aside :class="$style.editor">
    <h1>Редактировать ячейку</h1>
    <form :class="$style.form">
      <label :class="$style.option">
        Order:
        <input :class="$style.input" type="number" v-model="order" @input="changeProp">
      </label>
      <label :class="$style.option">
        Background-color:
        <input
          :class="$style.input"
          type="text"
          v-model="backgroundColor"
          @input="changeProp"
        >
      </label>
      <label :class="$style.option">
        Color:
        <input :class="$style.input" type="text" v-model="color" @input="changeProp">
      </label>
    </form>
  </aside>
</template>

<script>
import { eventBus } from "../main.js";

export default {
  created() {
    eventBus.$on("editCell", data => {
      this.order = data.styles.order;
      this.backgroundColor = data.styles.backgroundColor;
      this.color = data.styles.color;
    });
  },
  data() {
    return {
      order: null,
      backgroundColor: null,
      color: null
    };
  },
  methods: {
    changeProp() {
      eventBus.$emit("changeProp", this);
    }
  }
};
</script>

<style lang="sass" module>
	.editor
		/* Display & Box Sizing */
		display: flex
		flex-direction: column
		padding: 0 20px

		/* Color */
		background-color: #C861D3

	.form
		/* Display & Box Sizing */
		display: flex
		flex-direction: column
		align-items: stretch

	.option
		/* Display & Box Sizing */
		display: flex
		align-items: center
		justify-content: space-between
		padding: 10px
		margin-bottom: 10px
		border-radius: 40px

		/* color */
		background-color: #E8FB72	

		/* Other */
		cursor: pointer

	.input
		/* Display & Box Sizing */
		margin-left: 20px
		border: none

		/* Color */
		background-color: transparent

		/* Other */
		cursor: pointer
</style>
