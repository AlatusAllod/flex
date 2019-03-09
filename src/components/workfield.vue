<template>
  <main :class="$style.workfield">
    <div :class="$style.row" v-for="row in containers" :key="row.id">
      <container v-for="container in row" :container="container" :key="container.id"></container>
    </div>
  </main>
</template>

<script>
import container from "./container";
export default {
  components: {
    container
  },
  data() {
    return {
      containers: [
        [
          {
            id: 1,
            cells: 9,
            styles: {
              width: "300px",
              "background-color": "#DF004F"
            }
          },
          {
            id: 2,
            cells: 3,
            styles: {
              "flex-direction": "column",
              width: "100px",
              "background-color": "#74E600"
            },
            values: ["A", "B"]
          }
        ],
        [
          {
            id: 3,
            cells: 5,
            styles: {
              "flex-direction": "row-reverse",
              width: "500px",
              "background-color": "#FF3900"
            }
          }
        ],
        [
          {
            id: 4,
            cells: 5,
            styles: {
              width: "500px",
              "background-color": "#00B454"
            }
          }
        ]
      ]
    };
  }
};
</script>

<style lang="sass" module>
	.workfield
		/* Display & Box Sizing */
		display: flex
		flex-direction: column
		justify-content: space-between
		width: 500px
		height: 700px

		/* Text */
		user-select: none

		/* Shadow aka Border */
		box-shadow: 0 0 0 2px #000 inset

		/* Background */
		background-image: linear-gradient(#eee 1px, transparent 0px), linear-gradient(90deg, #eee 1px, transparent 0px)
		background-size: 100px 100px, 100px 100px
		background-position: -1px -1px, -1px 1px

	.row
		/* Display & Box Sizing */
		display: flex
		justify-content: space-between
		width: 100%
</style>
