<script setup>
    import { ref, defineEmits } from 'vue'
    const text = ref('')
    const amount = ref(0)

    const emit = defineEmits([
        'transactionSubmitted'
    ])

    const onSubmit = () => {
        const transactionData = {
            text: text.value,
            amount: parseFloat(amount.value),
        }

        emit('transactionSubmitted', transactionData)

        text.value = ''
        amount.value = ''
    }
</script>

<template>
    <h3>Add new transaction</h3>
    <form id ="form" @submit.prevent="onSubmit">
        <div class="form-control">
            <label for="text">Enter Transaction</label>
            <input type="text" id="text" v-model="text" placeholder="Enter Transaction..." />
        </div>
        <div class="form-control">
            <label for="amount">Enter Transaction Amount</label>
            <input type="text" id="amount" v-model="amount" placeholder="Enter Negative Value for Expenses" />
        </div>
        <button class="btn">Add Transaction</button>
    </form>
</template>