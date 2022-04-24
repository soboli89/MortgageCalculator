<template>
    <div>
        <h2>Banks list</h2>
        <div v-bind:key="bank.id" v-for="bank in banks">
          <BankItem v-bind:bank="bank" v-on:del-bank-item="delBankMethod" v-on:edit-bank-item="editBankmethod" v-on:select-bank-item="selectBankMethod"/>
        </div>
    </div>
</template>

<script>

import BankItem from './BankItem';

export default {
    name: "BankList",
    props: ["banks"],
    components: {
      BankItem
    },
    methods: {
      delBankMethod(id){
      this.$emit('del-bank-event', id);
      
    },
      editBankmethod(id){
        this.$emit('edit-bank-event', id)
      },
      selectBankMethod(id){
        this.$emit('select-bank-event', id)
      }
  }
}
</script>
