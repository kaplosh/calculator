<script>
export default {
  data() {
    return {
      curr_Value: "",
      first_Num: null,
      second_Num: null,
      operation: null,
      op_String: "",
      op_count: 0,
      result: null,
      result_state: false,
    };
  },
  methods: {
    add_Number(added_Num) {
      this.curr_Value = String(this.curr_Value) + String(added_Num);
      if(this.result_state === true){
        this.result_state = false
      }
    },

    save_Value() {
      this.first_Num = this.curr_Value;
      this.curr_Value = "";
      this.op_count++;

      if (this.result_state === true) {
        this.first_Num = this.result;
      }

      if(this.op_count > 1 && this.result_state === false){
        this.second_Num = this.curr_Value;
        this.make_result();
        this.second_Num = this.result;
        this.result = null;
      }


    },
    set_operation(param) {
      this.operation = param;

      if(this.operation === 1){
        this.op_String = "+"
      } else if (this.operation === 2) {
        this.op_String = "-"
      } else if (this.operation === 3){
        this.op_String = "*"
      } else if (this.operation === 4) {
        this.op_String = "/"
      }
    },
    make_result() {
      if(this.op_count === 1 ) {
        this.second_Num = this.curr_Value;
      }
      if(this.operation === 1) {
        this.result = Number(this.first_Num) + Number(this.second_Num);
        this.curr_Value = "";
      } else if(this.operation === 2 ) {
        this.result = Number(this.first_Num) - Number(this.second_Num);
        this.curr_Value = this.result;
        this.curr_Value = "";
      } else if (this.operation === 3 ) {
        this.result = Number(this.first_Num) * Number(this.second_Num);
        this.curr_Value = this.result;
        this.curr_Value = "";
      } else if (this.operation === 4) {
        this.result = Number(this.first_Num) / Number(this.second_Num);
        this.curr_Value = this.result;
        this.curr_Value = "";
      }
        this.result_state = true;

          },

    del_Single_Char(){
      this.curr_Value = this.curr_Value.slice(0, -1);
    },
    clear_all(){
      this.curr_Value = "";
      this.first_Num = null;
      this.second_Num = null;
      this.operation = null;
      this.result = null;
      this.op_String = "";
      this.op_count = 0;

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
        {{ curr_Value }} <br> {{ result }}
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
