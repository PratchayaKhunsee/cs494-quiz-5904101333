<template>
  <div class="color-box">
    <div
      class="square"
      :style="{
            backgroundColor: `rgba(${cCode.rgba[0]},${cCode.rgba[1]},${cCode.rgba[2]},${cCode.rgba[3]})`
        }"
    ></div>
    <div>
      <section>Color Name: {{cColor}}</section>
      <section>Category: {{cCategory}}</section>
      <section>Type: {{cType}}</section>
      <section>RGBA Code: {{cCode.rgba}}</section>
      <section>Hex Code: {{cCode.hex}}</section>
    </div>
  </div>
</template>
<style scoped>
.square {
  width: 100px;
  height: 100px;
  border: solid black 1px;
}
.color-box{
    display: inline-block;
    width: 150px;
}
</style>
<script>
export default {
  data() {
    return {
      cColor: this.colorName,
      cCategory: this.category,
      cType: this.type,
      cCode: {
        rgba: this.rgba,
        hex: this.hex
      }
    };
  },
  props: {
    colorName: {
      type: String,
      default: ""
    },
    category: {
      type: String,
      default: ""
    },
    type: {
      type: String,
      default: ""
    },
    rgba: {
      type: Array,
      default: () => [0, 0, 0, 1]
    },
    hex: {
      type: String,
      default: "#000"
    }
  }
};
</script>
