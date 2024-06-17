<template>
    <div class="income-list">
        <IncomeItem v-for="data in income" :key="data.id" :income="data" :removeItemWithId="removeItemWithId" />
    </div>
</template>
<script>
import IncomeItem from "./IncomeItem.vue";
export default {
    name: 'IncomeList',
    props: {
        income: Object,
        removeItem: Function
    },
    components: {
        IncomeItem,
    },
    methods: {
        removeItemWithId(id) {
            // alert(id);
            this.removeItem(id);
        }
    }
}
</script>
<style scoped>
.income-list {
    margin-top: 30px;
    padding: 15px;
}
</style>