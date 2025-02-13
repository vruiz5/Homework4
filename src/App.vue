<script setup>
  import Header from './components/Header.vue';
  import Balance from './components/Balance.vue';
  //import IncomeExpenses from './components/IncomeExpenses.vue';
  //import TransactionList from "./components/TransactionList.vue";
  //import AddTransaction from "./components/AddTransaction.vue";
  import { ref, computed } from 'vue';

  const transcactions = ref([
    {id: 1, text: 'Paycheck', amount: 700.00},
    {id: 2, text: 'Water Bill', amount: -72.83},
    {id: 3, text: 'Electric Bill', amount: -153.89},
    {id: 4, text: 'Returned Item', amount: 20.00}
  ])

  const sum = computed(() => {
      return transcactions.value.reduce((acc, x) => {
          return acc + x.amount
      }, 0)
  })

</script>

<template>
    <Header></Header>
    <div class="container">
        <Balance :total="sum"></Balance>
        <IncomeExpenses></IncomeExpenses>
        <TransactionList></TransactionList>
        <AddTransaction></AddTransaction>
    </div>
</template>