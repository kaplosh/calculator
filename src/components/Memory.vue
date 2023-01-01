<script>
export default {
  name: "Memory",
  props:[
    'curr_Value'
  ],

  data() {

    return {
      memory_List: [],
      memory_Count: 0,
    };
  },
  methods: {
    add_M() {
      this.memory_Count++;
      this.memory_List.push(Number(this.$props.curr_Value));
    },
    clear_M() {
      this.memory_List = [];
      this.memory_Count = 0;
    },
    sort_M() {
      this.memory_List.sort(function (x, y) {
        return y - x;
      });
    },
    push_M() {
      console.log(this.memory_List[this.memory_List.length - 1]);
      if (this.memory_Count >= 1) {
        this.memory_Count--;
        this.$props.curr_Value = this.memory_List[this.memory_List.length - 1];
        this.memory_List = this.memory_List.slice(0, -1);
      }

    },
  },

};
</script>

<template>
  <button type="button" @click="add_M()" class="btn btn-outline-light">CM+</button>
  <button type="button" @click="push_M()" class="btn btn-outline-light">CM-Push</button>
  <button type="button" @click="clear_M()" class="btn btn-outline-light">CM-Clear</button>
  <button type="button" @click="sort_M()" class="btn btn-outline-light">CM-Sort</button>

  <div v-if="memory_Count <= 1">
    Uložená hodnota v paměti je {{ memory_List }}
  </div>
  <div v-else="memory_Count >= 2">
    Uložené hodnoty v paměti jsou {{ memory_List }}
  </div>
</template>




<style scoped>

</style>