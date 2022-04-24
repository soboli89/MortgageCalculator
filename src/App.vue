<template>
  <div id="app">
    <AddBank v-on:add-bank-event="addBank" v-bind:editBank="editBank" v-on:edit-bank-event="editBankEvent"/>
    <div>
      <BankList v-bind:banks="banks" v-on:del-bank-event="deleteBankItem" v-on:edit-bank-event="editBankItem" v-on:select-bank-event="selectBankItem"/>
    </div>
      <Calculator v-model="selectBank.title" v-on:select-bank-item="selectBankItem" v-bind:selectBank="selectBank"></Calculator>
  </div>
</template>

<script>
import BankList from './components/BankList'
import AddBank from './components/AddBank.vue'
import Calculator from './components/Calculator.vue'


export default {
  name: 'App',
  components: {
    BankList,
    // eslint-disable-next-line
    AddBank,
     // eslint-disable-next-line
    Calculator
  },
  data (){
    return {
      banks: [],
      editBank: {
        title: '',
        rate: '',
        maxLoan: '',
        minPayment: '',
        term: '',
        id: ''
      },
      selectBank: {
        title: '',
        rate: '',
        maxLoan: '',
        minPayment: '',
        term: '',
        id: ''
      }
    }
  },
  methods: {
    addBank(newBank){
      this.banks = [...this.banks, newBank]
    },
    
    deleteBankItem(id){
      this.banks = this.banks.filter(bank=> bank.id !== id);
    },
    editBankItem(id){
      let objIndex = this.banks.findIndex(obj=> obj.id ===id);
      this.editBank.title = this.banks[objIndex].title;
      this.editBank.rate = this.banks[objIndex].rate;
      this.editBank.maxLoan = this.banks[objIndex].maxLoan;
      this.editBank.minPayment = this.banks[objIndex].minPayment;
      this.editBank.term = this.banks[objIndex].term;
      this.editBank.id = id;
    },
    editBankEvent(BankItem) {
      let objIndex = this.banks.findIndex(obj => obj.id === BankItem.id)
      this.banks[objIndex].title = BankItem.title;
      this.banks[objIndex].rate = BankItem.rate;
      this.banks[objIndex].maxLoan = BankItem.maxLoan;
      this.banks[objIndex].minPayment = BankItem.minPayment;
      this.banks[objIndex].term = BankItem.term;
    },
    selectBankItem(id){
      let objIndex = this.banks.findIndex(obj=> obj.id ===id);
      this.selectBank.title = this.banks[objIndex].title;
      this.selectBank.rate = this.banks[objIndex].rate;
      this.selectBank.maxLoan = this.banks[objIndex].maxLoan;
      this.selectBank.minPayment = this.banks[objIndex].minPayment;
      this.selectBank.term = this.banks[objIndex].term;
      this.selectBank.id = id;
    },
  },
  watch: {
    banks: {
      handler() {
        localStorage.setItem('banks', JSON.stringify(this.banks))
      },
      deep: true
    }
},
  mounted() {
    if (localStorage.getItem("banks")){
      this.banks = JSON.parse(localStorage.getItem("banks"))
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
