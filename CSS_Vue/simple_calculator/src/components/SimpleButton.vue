<template>
  <button @click="calculate">
    {{beschriftung}}
  </button>
</template>

<script>


export default {
  emits: ['calculate'],
  name:'SimpleButton',
  props: {
    beschriftung: String
  },
  data() {
    return [];
  },
  methods: {
    calculate() {
      this.$emit('calculate', this.beschriftung);
    }
  }
}
</script>