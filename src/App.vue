<script>
export default {
  data() {
    return {
      curr_Value: "",
      first_Num: null,
      second_Num: null,
    };
  },
  methods: {
    add_Num(added_Num) {
      this.curr_Value = String(this.curr_Value) + String(added_Num);
    },

    addittion() {
      console.log("addittion");
      this.first_Num = this.curr_Value;
      //this.curr_Value = "";
      console.log(this.first_Num);
    },
  },
};
console.log("Hi");
</script>

<template>
  <header>Kamilova Kalkulačka</header>
  <main>
    <div class="container">
      <div>
        <button type="button" @click="add_Num(9)" class="btn btn-outline-light">
          9
        </button>
        <button type="button" @click="add_Num(8)" class="btn btn-outline-light">
          8
        </button>
        <button type="button" @click="add_Num(7)" class="btn btn-outline-light">
          7
        </button>
        <button type="button" @click="add_Num(6)" class="btn btn-outline-light">
          6
        </button>
        <button type="button" @click="add_Num(5)" class="btn btn-outline-light">
          5
        </button>
        <button type="button" @click="add_Num(4)" class="btn btn-outline-light">
          4
        </button>
        <button type="button" @click="add_Num(3)" class="btn btn-outline-light">
          3
        </button>
        <button type="button" @click="add_Num(2)" class="btn btn-outline-light">
          2
        </button>
        <button type="button" @click="add_Num(1)" class="btn btn-outline-light">
          1
        </button>
        <button type="button" @click="add_Num(0)" class="btn btn-outline-light">
          0
        </button>
      </div>
      <div>
        <button type="button" @click="addittion()" class="btn btn-outline-light">+</button>
        <button type="button" class="btn btn-outline-light">-</button>
        <button type="button" class="btn btn-outline-light">*</button>
        <button type="button" class="btn btn-outline-light">/</button>
        <button type="button" class="btn btn-outline-light">Del</button>
        <button type="button" class="btn btn-outline-light">Clear</button>
        <button type="button" class="btn btn-outline-light">=</button>
      </div>
      <div>
        {{ curr_Value }}
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
