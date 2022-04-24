<template>
    <div>
        <form @submit="addBank">
            <input type="text" name="title" v-model="title" placeholder="Add Bank">
           <input type="number" name="rate" v-model="rate" placeholder="Add rate">
            <input type="number" name="Max-loan" v-model="maxLoan" placeholder="Add maximum loan">
            <input type="number" name="min-payment-loan" v-model="minPayment" placeholder="Add minimum payment">
            <input type="number" name="term" v-model="term" placeholder="Add loan term">
            <button type="submit">Add Bank</button>
        </form>
    </div>
</template>

<script>
export default {
    name: "AddBank",
    props: ['editBank','selectBank'],
   
    data () {
        return {
            title: '',
            rate: '',
            maxLoan: '',
            minPayment: '',
            term: '',
            id: '',
            edit: false
        }
    },
    methods:{
        addBank(e){
            e.preventDefault();
            if (this.edit === false){
             const newBank = {
                title: this.title,
                rate: this.rate,
                maxLoan: this.maxLoan,
                minPayment: this.minPayment,
                term: this.term,
                id: Math.floor(Math.random()*100)
            };
            if(newBank.title !== ''){
                this.$emit('add-bank-event', newBank);
            }   
            this.title='',
            this.rate = '',
            this.maxLoan= '',
            this.minPayment = '',
            this.term = ''
            }else{
                const BankItem = {
                    title: this.title,
                    rate: this.rate,
                    maxLoan: this.maxLoan,
                    minPayment: this.minPayment,
                    term: this.term,
                    id: this.id
                }
                this.$emit('edit-bank-event', BankItem);
                this.title = '';
                this.rate = '';
                this.maxLoan = '';
                this.minPayment = '';
                this.term = '';
                this.edit = false
            }
        },
    },
    watch: {
        editBank:{
            handler (){
                this.title = this.editBank.title;
                this.rate = this.editBank.rate;
                this.maxLoan = this.editBank.maxLoan;
                this.minPayment = this.editBank.minPayment;
                this.term = this.editBank.term;
                this.id = this.editBank.id;
                this.edit = true;
            },
            deep: true
        },
        title: {
            handler() {
                if (this.title === ''){
                    this.edit = false;
                }
            }
        },
        rate: {
            handler() {
                if (this.rate === ''){
                    this.edit = false;
                }
            }
        },
        maxLoan: {
            handler() {
                if (this.maxLoan === ''){
                    this.edit = false;
                }
            }
        },
        minPayment: {
            handler() {
                if (this.minPayment === ''){
                    this.edit = false;
                }
            }
        },
        term: {
            handler() {
                if (this.term === ''){
                    this.edit = false;
                }
            }
        }
    }
}
</script>