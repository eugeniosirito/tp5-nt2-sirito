<template>
  <section>
    <div
      class="square"
      @click="resolver()"
      :juegoFinalizado="setjuegoFinalizado(juegoFinalizado)"
      :style="getStyle(white)"
    ></div>
    <!--  :style="{background: color}" -->
  </section>
</template>


<script>
export default {
  name: "src-componentes-square",
  props: ["color", "pickedColor", "resetEstado", "juegoFinalizado"],

  mounted() {},

  data() {
    return {
      white: false,
    };
  },
  methods: {
    setjuegoFinalizado(estado) {
      if (estado) {
        this.white = !estado;
      }
    },

    setWhite(estado) {
      if (estado) {
        this.white = false;
      }
    },

    getStyle(estado) {
      return {
        backgroundColor: !estado ? this.color : "white",
      };
    },

    resolver() {
      if (this.pickedColor == this.color) {
        this.$emit("resultadoHijo", true);
        this.white = false;
      } else {
        this.white = true;
      }
    },
  },
  computed: {},
};
</script>

<style scoped lang="css">
.square {
  width: 30%;

  padding-bottom: 30%;
  float: left;
  margin: 1.66%;
  border-radius: 10%;
  transition: background 0.8s;
  -webkit-transition: background 0.8s;
  -moz-transition: background 0.8s;
}
</style>
