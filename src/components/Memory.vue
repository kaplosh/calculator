<script>
export default {
  name: "Memory",
  props:[
    'currentValue',
  ],

  data() {

    return {
      memoryList: [],
      memoryCount: 0,
    };
  },
  methods: {
    add_M() {
      this.memoryCount++;
      this.memoryList.push(Number(this.$props.currentValue));
    },
    clear_M() {
      this.memoryList = [];
      this.memoryCount = 0;
    },
    sort_M() {
      this.memoryList.sort(function (x, y) {
        return y - x;
      });
    },
    push_M() {
      //console.log(this.memoryList[this.memoryList.length - 1]);
      if (this.memoryCount >= 1) {
        this.memoryCount--;
        let pushedValue = this.memoryList[this.memoryList.length - 1];
        console.log("constis", pushedValue);
        this.memoryList = this.memoryList.slice(0, -1);
        this.$emit("push", pushedValue );
      }

    },
  },

};
</script>

<template>
  <button type="button" @click="add_M()" class="btn btn-outline-light">M+</button>
  <button type="button" @click="push_M()" class="btn btn-outline-light">M-Push</button>
  <button type="button" @click="clear_M()" class="btn btn-outline-light">M-Clear</button>
  <button type="button" @click="sort_M()" class="btn btn-outline-light">M-Sort</button>

  <div v-if="memoryCount <= 1">
    Uložená hodnota v paměti je {{ memoryList }}
  </div>
  <div v-else="memoryCount >= 2">
    Uložené hodnoty v paměti jsou {{ memoryList }}
  </div>
</template>




<style scoped>

</style>