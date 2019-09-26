<template>
  <div class="hello">
    <tools-info-box v-for="item in types" :key="item" :type="item">
      {{item}}
    </tools-info-box>

  </div>
</template>

<script>
import InfoSelectedBox from "./InfoSelectedBox.vue";
import ToolsInfoBox from './ToolsInfoBox';

export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  components: {
    InfoSelectedBox,
    ToolsInfoBox,
  },
  data() {
    return {
      checked1: true,
      checked2: false,
      checked3: false,
      types: ['point', 'distance', 'area', 'clear', 'viewshed', 'profile', 'satelite']
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  position: absolute;
  height: 500px;
  width: 600px;
  margin: 0;
  border: solid 2px rgb(27, 209, 255);
  background: rgba(255, 255, 255, 0.616);
}
</style>
