<template>
  <div class="inner-container">

    <BaseRadioGroup
      title="Mode"
      name="mode"
      horizontal="true"
      buttons="true"
      :options="[{
        label: 'Stone / Pound',
        id: 'stone-pound',
        value: 'stone'
      },{
        label: 'Pound',
        id: 'pound',
        value: 'lb'
      }]"
      @change="changeMode()"
      v-model="mode"
    />

    <BaseInput
      label="Kilos (kg)"
      id="kg"
      type="number"
      v-model="kg"
      @input="weightCalculate('kg')"
    />

    <BaseInput
      label="Stone (st)"
      id="stone"
      type="number"
      v-model="stone"
      @input="weightCalculate('stone')"
      v-if="mode == 'stone'"
    />
    <BaseInput
      label="Pound (lb)"
      id="lb"
      type="number"
      v-model="lb"
      @input="weightCalculate('lb')"
    />

  </div>
</template>

<script>
  export default {
    data() {
      return {
        kg: 0,
        stone: 0,
        lb: 0,
        mode: 'stone'
      }
    },
    methods: {
      weightCalculate(type) {
        if (type == 'kg' && isNaN(this.kg)) {
          this.kg = 0
        } else if (type == 'stone' && isNaN(this.stone)) {
          this.stone = 0
        } else if (type == 'lb' && isNaN(this.lb)) {
          this.lb = 0
        }

        if (type == 'kg') {
          let lb = Math.floor(this.kg * 2.205)
          if (this.mode == 'lb') {
            this.lb = lb
          } else {
            this.stone = Math.floor(lb / 14)
            this.lb = Math.floor(lb - (this.stone * 14))
          }
        } else if (type == 'lb' || type == 'stone') {
          let lb = this.lb
          if (this.mode == 'stone') {
            lb = (this.stone * 14) + parseInt(this.lb)
          }
          this.kg = (lb / 2.205).toFixed(2)
        }
      },
      changeMode() {
        this.weightCalculate('kg')
      }
    }
  }
</script>
