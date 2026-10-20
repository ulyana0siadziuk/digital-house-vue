<script>
export default {
  name: 'QuantitySelector',
  props: {
    min: {
      type: Number,
      default: 1,
    },
    max: {
      type: Number,
      default: 99,
    },
  },
  data() {
    return {
      quantity: this.min,
    }
  },
  methods: {
    decrease() {
      if (this.quantity > this.min) {
        this.quantity -= 1
        this.$emit('change', this.quantity)
      }
    },
    increase() {
      if (this.quantity < this.max) {
        this.quantity += 1
        this.$emit('change', this.quantity)
      }
    },
  },
}
</script>

<template>
  <div class="selector">
    <button
      type="button"
      class="control"
      :disabled="quantity <= min"
      @click="decrease"
    >
      −
    </button>
    <span class="value">{{ quantity }}</span>
    <button
      type="button"
      class="control"
      :disabled="quantity >= max"
      @click="increase"
    >
      +
    </button>
  </div>
</template>

<style scoped>
.selector {
  align-self: center;
  display: flex;
  align-items: stretch;
  box-sizing: border-box;
  width: 133px;
  height: 43px;
  overflow: hidden;
  border: 1.5px solid #0ea5e9;
  border-radius: 14px;
}

.control {
  flex: 1;
  border: none;
  background: #ffffff;
  color: #0ea5e9;
  font-size: 18px;
  line-height: 1;
  cursor: pointer;
}

.control:disabled {
  color: #7dd3fc;
  cursor: not-allowed;
}

.value {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  border-left: 1.5px solid #0ea5e9;
  border-right: 1.5px solid #0ea5e9;
  color: #111827;
  font-weight: 600;
}
</style>
