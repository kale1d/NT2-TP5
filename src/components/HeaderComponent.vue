<template lang="html">

  <section class="header-component">
    <div id="header">
      <h1>The Great <br>
        <span id="colorDisplay">RGB</span>
        <h2>{{ pickedColor }}</h2>
        <br>
        Guessing Game
      </h1>
    </div>
  </section>

</template>

<script lang="js">

export default {
  name: 'header-component',
  props: ['pickedColor'],
  mounted() {

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
#header {
  transition: all 0.3s;
  background: steelblue;
  text-transform: uppercase;
  text-align: center;
  margin: 0;
  color: white;
}

h1 {
  font-weight: normal;
  line-height: 1.1;
  padding: 20px 0;

}

#colorDisplay {
  font-size: 200%;
}
</style>
