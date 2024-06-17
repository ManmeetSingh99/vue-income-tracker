<template>
    <form v-on:submit.prevent="formHandler()">
        <input type="text" v-model="formData.desc" placeholder="Description...">
        <input type="number" v-model="formData.value" placeholder="Value...">
        <input type="date" v-model="formData.date" placeholder="Date...">
        <input type="submit" value="SUBMIT">
    </form>
</template>
<script>
export default {
    name: 'FormComponent',
    props: {
        addIncome: Function
    },
    data() {
        return {
            formData: {
                desc: null,
                value: null,
                date: null,
            }
        }
    },
    methods: {
        formHandler() {
            this.addIncome(this.formData);
            this.formData.desc = null;
            this.formData.value = null;
            this.formData.date = null;
        },

    }
}
</script>
<style scoped>
form {
    display: flex;
    justify-content: center;
    margin-top: 30px;
}

form input {
    color: #888;
    border: none;
    outline: none;
    font-size: 20px;
}

form input::placeholder {
    color: #AAA;
}

form input:not([type="submit"]) {
    display: block;
    background: #FFF;
    border: none;
    outline: none;
    padding: 5px 15px;
}

form input[type="submit"] {
    display: block;
    background: none;
    border: none;
    outline: none;

    color: #FFF;
    font-weight: 500;
    text-shadow: 0px 1px 3px rgba(0, 0, 0, 0.2);
    padding: 5px 15px;
    background-color: #FFCE00;

    cursor: pointer;
}

form input:first-of-type {
    border-radius: 8px 0px 0px 8px;
}

form input:last-of-type {
    border-radius: 0px 8px 8px 0px;
}
</style>