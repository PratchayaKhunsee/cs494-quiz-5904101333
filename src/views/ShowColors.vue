<template>
  <div>
    <h1>Show Color</h1>
    <div v-for="(color,index) in colors" :key="index">
      <color-box
        :color-name="color.color"
        :category="color.category"
        :type="color.type"
        :rgba="color.code.rgba"
        :hex="color.code.hex"
      ></color-box>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import ColorBox from "@/components/ColorBox.vue";
const Firebase = require("firebase");

const config = {
  apiKey: "AIzaSyBFK_m2HR1-y1g7LJm1GibkI_LPsHRX6Qg",
  authDomain: "quiz-vue-colors-5904101333.firebaseapp.com",
  databaseURL: "https://quiz-vue-colors-5904101333.firebaseio.com",
  projectId: "quiz-vue-colors-5904101333",
  storageBucket: "quiz-vue-colors-5904101333.appspot.com",
  messagingSenderId: "131685760984"
};

export default {
  name: "showcolors",
  components: {
    "color-box": ColorBox
  },
  data() {
    return {
      colors: []
    };
  },
  mounted() {
    Firebase.initializeApp(config);
    var database = Firebase.database();
    var rootRef = database.ref();
    var colorsRef = rootRef.child('colors');
    var colors = this.colors;
    colorsRef.once('value',function(snapshot){
      // console.log(snapshot.val());
      for(let color of snapshot.val()){
        colors.push(color);
      }
    });
  }
};
</script>