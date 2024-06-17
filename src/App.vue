<template>
  <HeaderComponent :totalIncome="totalIncome" />
  <FormComponent :addIncome="addIncome" />
  <IncomeList :income="sortedIncome" :removeItem="removeItem" />
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import FormComponent from "./components/FormComponent.vue";
import IncomeList from "./components/IncomeList.vue";
import { computed } from "vue";
export default {
  name: 'App',
  components: {
    HeaderComponent,
    FormComponent,
    IncomeList
  },
  data() {
    return {
      income: [

      ],
      totalIncome: computed(() => {
        let temp = 0;
        if (this.income.length > 0) {
          for (let i = 0; i < this.income.length; i++) {
            temp = temp + this.income[i].value;
          }
        }
        return temp;
      }),
      sortedIncome: computed(() => {
        let temp = [];
        temp = this.income.sort(function (a, b) {
          return b.date - a.date;
        });
        return temp;
      })
    }
  },
  methods: {
    addIncome(data) {
      let d = data.date.split("-");
      let newD = new Date(d[0], d[1], d[2]);

      // console.log("App: ", data);
      this.income = [...this.income, {
        id: Date.now(),
        desc: data.desc,
        value: data.value,
        date: newD.getTime()
      }];

      console.log(this.sortedIncome);
    },
    removeItem(id) {
      this.income = this.income.filter(item => item.id !== id);
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

body {
  background-color: #eee;
}
</style>
