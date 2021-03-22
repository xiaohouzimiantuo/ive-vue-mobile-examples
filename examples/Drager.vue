<template>
  <div class="drager">
    <ive-drager :isFixed="false" aside="h" class="test_drager"></ive-drager>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { IveDrager } from "ive-vue-mobile";
export default defineComponent({
  props: {
    
  },
  setup(props) {

  },
  
  components: {
    IveDrager
  },
});
</script>

<style lang="scss" scoped>
.drager{
  position: relative;
  width: 300px;
  height: 300px;
  margin: 40px auto;
  background: orange;
}
.test_drager{
  width: 100px;
  height: 100px;
  background: red;
}
</style>
