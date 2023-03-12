<template>
  <HeaderView :totalIncome="this.state.totalIncome" />
</template>

<script>
import { computed } from 'vue';
import HeaderView from './components/HeaderView.vue'

export default {
  name: "App",
  data() {
    return {
      state: {
        income: [{
          value: 400
        },
        {
          value: 500
        }],
        totalIncome: computed(() => {
          let temp = 0

          if (this.state.income.length > 0) {
            for (let i = 0; i < this.state.income.length; i++) {
              temp += this.state.income[i].value
            }
          }

          return temp
        })
      }
    }
  },
  components: { HeaderView },
  // computed: {
  //   totalIncome: {
  //     get() {
  //       return this.totalIncome
  //     },
  //     set(value) {

  //     }
  //   }
  // }

}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;
}

body {
  background: #EEE;
}
</style>
