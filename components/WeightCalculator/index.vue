<template>
  <div class="inner-container">

    <BaseInput label="Kilograms" id="kg" type="number" v-model="kg" @input="weightCalculate('kg')" />

    <BaseInput label="Pounds" id="lb" type="number" v-model="lb" @input="weightCalculate('lb')" />

  </div>
</template>

<script>
  export default {
    data() {
      return {
        kg: 0,
        lb: 0
      }
    },
    methods: {
      weightCalculate(type) {
        let value = 0
        if (type == 'kg') {
          value = this.kg
        } else if (type == 'lb') {
          value = this.lb
        }

        if (isNaN(value)) {
          value = 0
          if (type == 'kg') {
            this.kg = 0
          } else if (type == 'lb') {
            this.lb = 0
          }
        }

        if (type == 'kg') {
          this.lb = (this.kg * 2.205).toFixed(2)
        } else if (type == 'lb') {
          this.kg = (this.lb / 2.205).toFixed(2)
        }
      }
    }
  }
</script>
