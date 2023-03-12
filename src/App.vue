<template>
  <HeaderView :totalIncome="this.state.totalIncome" />
  <FormView  @add-income="this.AddIncome"/>
  <IncomeList :state="state"/>
</template>

<script>
import { computed } from 'vue';
import HeaderView from './components/HeaderView.vue'
import FormView from './components/FormView.vue'
import IncomeList from './components/IncomeList.vue'
export default {
  name: "App",
  data() {
    return {
      state: {
        income: [],
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
  components: { HeaderView, FormView, IncomeList },

  methods: {
    AddIncome(data){
      // Date format
      let d = data.date.split("-");
      let newD = new Date(d[0], d[1], d[2])

      this.state.income = [...this.state.income, {
        id: Date.now(),
        desc: data.desc,
        value: data.value,
        date: newD.getTime()
      }]
      
      console.log(this.state.income)
    }
  }

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
