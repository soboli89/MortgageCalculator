<template>
    <div>
        <h2>You selected for calculation: {{selectBank.title}} bank</h2>
        <form @submit.prevent="calculate">
            <Label>Initital loan</Label>
            <input type="number" name="loan" v-model="loan" placeholder="Add Initial loan"><br/>
            <Label>Down payment</Label>
            <input type="number" name="downPayment" v-model="downPayment" placeholder="Add down payment"><br/>
            <button type="submit">Calculate</button>
        </form><br/>
          <p>Your monthly payment: {{monthlyPayment }}</p>
    </div>
</template>

<script>
export default {
    // eslint-disable-next-line
    name: 'Calculator',
    data(){
         return {
              loan: '',
              downPayment: '',
              monthlyPayment: '',           
          }
      },
    props: ['selectBank'],
    methods: {
        calculate() { 
            if((parseInt(this.loan))>(parseInt(this.selectBank.maxLoan))) {
                this.monthlyPayment = "Sorry you can't get a loan";
            } else if (parseInt(this.downPayment)<parseInt(this.selectBank.minPayment))
                {this.monthlyPayment = "Sorry you can't get a loan";}
                    else{this.monthlyPayment = ((this.loan-this.downPayment)*(this.selectBank.rate/12)*Math.pow((1+this.selectBank.rate/12),this.selectBank.term))/(Math.pow((1+this.selectBank.rate/12),this.selectBank.term)-1)} 
                        }
        }
    }
</script>