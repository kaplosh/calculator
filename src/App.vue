<script>

import Memory from "./components/Memory.vue";
export default {

  components:{
    Memory
  },

  data() {
    return {
      currentValue: "",
      firstNumber: null,
      secondNumber: null,
      operation: null,
      opString: "",
      result: null,
      memory: null,
      memoryList: [],
      memoryCount: 0,
    };
  },
  methods: {
    add_Number(added_Num) {
      this.currentValue = String(this.currentValue) + String(added_Num);
    },

    save_Value() {
      this.firstNumber = this.currentValue;
      this.currentValue = "";
      console.log(this.currentValue);
      console.log(this.firstNumber);

      if(this.result !== null){
        this.firstNumber = this.result;
      }
    },
    set_operation(param) {
      this.operation = param;
      if(this.operation === 1){
        this.opString = "+"
      } else if (this.operation === 2) {
        this.opString = "-"
      } else if (this.operation === 3){
        this.opString = "*"
      } else if (this.operation === 4) {
        this.opString = "/"
      }
    },
    make_result() {
      this.secondNumber = this.currentValue;
      if(this.operation === 1) {
        this.result = Number(this.firstNumber) + Number(this.secondNumber);

        this.currentValue = "";
      } else if(this.operation === 2 ) {
        this.result = Number(this.firstNumber) - Number(this.secondNumber);
        this.currentValue = this.result;
        this.currentValue = "";
      } else if (this.operation === 3 ) {
        this.result = Number(this.firstNumber) * Number(this.secondNumber);
        this.currentValue = this.result;
        this.currentValue = "";
      } else if (this.operation === 4) {
        this.result = Number(this.firstNumber) / Number(this.secondNumber);
        this.currentValue = this.result;
        this.currentValue = "";

      }
      this.firstNumber = null;
      this.secondNumber = null;
    },
    del_Single_Char(){
      this.currentValue = this.currentValue.slice(0, -1);
    },
    clear_all(){
      this.currentValue = "";
      this.firstNumber = null;
      this.secondNumber = null;
      this.operation = null;
      this.result = null;
      this.opString = "";
    },
    add_M() {
      this.memoryCount++;
      this.memoryList.push(Number(this.currentValue));
    },
    clear_M(){
      this.memoryList = [];
      this.memoryCount = 0;
    },
    sort_M(){
      this.memoryList.sort(function(x,y){
        return y - x;
      });
    },
    push_M(){
      console.log(this.memoryList[this.memoryList.length -1]);
      if(this.memoryCount >= 1) {
        this.memoryCount--;
        this.currentValue = this.memoryList[this.memoryList.length -1];
        this.memoryList = this.memoryList.slice(0, -1);
      }
    },
    onPush(pushedValue){
      this.currentValue = pushedValue;
    }
  },
};
console.log("Hi");
</script>

<template>
  <header>Kamilova Kalkulačka</header>
  <main>
    <div class="container">
      <div>
        <button type="button" @click="add_Number(9)" class="btn btn-outline-light">
          9
        </button>
        <button type="button" @click="add_Number(8)" class="btn btn-outline-light">
          8
        </button>
        <button type="button" @click="add_Number(7)" class="btn btn-outline-light">
          7
        </button>
        <button type="button" @click="add_Number(6)" class="btn btn-outline-light">
          6
        </button>
        <button type="button" @click="add_Number(5)" class="btn btn-outline-light">
          5
        </button>
        <button type="button" @click="add_Number(4)" class="btn btn-outline-light">
          4
        </button>
        <button type="button" @click="add_Number(3)" class="btn btn-outline-light">
          3
        </button>
        <button type="button" @click="add_Number(2)" class="btn btn-outline-light">
          2
        </button>
        <button type="button" @click="add_Number(1)" class="btn btn-outline-light">
          1
        </button>
        <button type="button" @click="add_Number(0)" class="btn btn-outline-light">
          0
        </button>
      </div>
      <div>
        <button type="button" @click="save_Value(); set_operation(1)" class="btn btn-outline-light">+</button>
        <button type="button" @click="save_Value(); set_operation(2)" class="btn btn-outline-light">-</button>
        <button type="button" @click="save_Value(); set_operation(3)" class="btn btn-outline-light">*</button>
        <button type="button" @click="save_Value(); set_operation(4)" class="btn btn-outline-light">/</button>
        <button type="button" @click="del_Single_Char()" class="btn btn-outline-light">Del</button>
        <button type="button" @click="clear_all()" class="btn btn-outline-light">Clear</button>
        <button type="button" @click="make_result()" class="btn btn-outline-light">=</button>
      </div>
      <div>
        <Memory :currentValue="currentValue" :pushedValue="pushedValue" @push="onPush" />
      </div>
      <div>
        Aktuální naklikaná hodnota je {{ currentValue }} <br> Výsledek je {{ result }}
      </div>
    </div>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
