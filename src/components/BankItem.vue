<template>
    <div class="float-left">
         <span class="float-right">
           Title: {{bank.title}}<br/>
            Interest rate: {{bank.rate}} %<br/>
            Maximum loan: {{bank.maxLoan}} UAH<br/>
            Minimum down payment: {{bank.minPayment}} UAH <br/>
            Loan term: {{bank.term}} month<br/>
                <button>
                    <i class="glyphicon glyphicon-" @click="$emit('select-bank-item', bank.id)">select</i>
                </button>
                <button>
                    <i class="glyphicon glyphicon-pencil" @click="$emit('edit-bank-item', bank.id)">edit</i>
                </button>
                <button>
                    <i class="glyphicon glyphicon-trash" @click="$emit('del-bank-item', bank.id)">delete</i>
                </button>
                
    </span>
    </div>
</template>
<script>
    export default{
        name: 'BankItem',
        props: ["bank"]
    }
</script>