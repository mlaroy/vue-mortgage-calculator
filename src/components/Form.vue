<template>
  <div>
    <div class="payment">
      <span class="total">{{ payment }}</span>
      {{ period }}
    </div>
    <form>
      <div>
        <label for="principal">Principal Amount</label>
        <input type="number" id="principal" v-model="principal" step="1000" placeholder="0" />
      </div>
      <div>
          <label for="interestRate">Interest Rate</label>
          <input type="number" id="interestRate" v-model="interestRate" step=".01" placeholder="3.9%" />
      </div>
      <div>
        <label for="frequency">Payment Frequency</label>
        <select v-model="frequency" id="frequency" ref="frequency">
          <option v-for="item in frequencies" :value="item.value" :key="item.value">{{ item.label }}</option>
        </select>
      </div>
      <div>
        <label for="amortization">Amortization</label>
        <select id="amortization" v-model="amortization">
          <option value="1">1 Year</option>
          <option value="3">3 Years</option>
          <option value="5">5 Years</option>
          <option value="10">10 Years</option>
          <option value="15">15 Years</option>
          <option value="25">25 Years</option>
          <option value="30">30 Years</option>
        </select>
      </div>
    </form>

  </div>
</template>

<script>

export default {
  name: 'Form',
  props: {
    msg: String
  },
  data() {
    return {
      amortization: 30,
      principal: 100000,
      interestRate: 3.9,
      frequency: 12,
      frequencies: [
        {
          value: 12,
          label: 'Monthly',
        },
        {
          value: 24,
          label: 'Semi-monthly',
        },
        {
          value: 52,
          label: 'Weekly',
        },
        {
          value: 26,
          label: 'Bi-weekly'
        }
      ]
    }
  },
  computed: {
    payment() {

      const interest = (this.interestRate / this.frequency) / 100;
      const numPayments = this.frequency * this.amortization;

      // payment value
      let output = (this.principal * interest) / (1 - Math.pow(1 + interest, -numPayments));
      output = ( isNaN(output) ) ? 0 : output;

      return output.toLocaleString('en-US', {
        style: 'currency',
        currency: 'USD'
      })
    },
    period() {
      const current = this.frequencies.find( frequency => frequency.value == this.frequency );
      return current.label;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

select,
input {
  /* border: 1px solid #999; */
  border: none;
  border-radius: 4px;
  padding: 0.75rem;
  font-size: 16px;
  width: 100%;
}

form {
  display: grid;
  grid-gap: 2rem;
  grid-template-columns: repeat(2, minmax(400px, 1fr) );
   /* padding: 25px; */
}

form div {
  display: flex;
  flex-direction: column;
  max-width: 100%;
  min-width: 0;
}

.payment {
  background: white;
  border-radius: 3px;
  padding: 25px;
  text-align: center;
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 4rem;
}

.total {
  display: block;
  font-size: 56px;
}

</style>
