<template lang="html">

  <section class="container-component">
    <div id="container">
      <SquareComponent v-for="(square, index) in squareQty" :key="index" :color="colors[index]" :pickedColor="
      pickedColor" @selectedColor="selectedColor = $event" />
    </div>

  </section>

</template>

<script lang="js">
import SquareComponent from './SquareComponent.vue';

export default {
  name: 'container-component',
  components: { SquareComponent },
  props: ["squareQty", "colors", 'pickedColor'],
  updated() {
  },
  data() {
    return {
    }
  },
  methods: {
  },
  computed: {


  }
}


</script>

<style scoped lang="css">
#container {
  margin: 20px auto;
  max-width: 600px;
}
</style>
