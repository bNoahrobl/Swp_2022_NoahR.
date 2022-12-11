<template>
  <button @click="calculate">
    {{beschreibung}}
  </button>
</template>

<script>


export default {
  emits: ['calculate'],
  name:'SimpleButton',
  props: {
    beschreibung: String
  },
  data() {
    return [];
  },
  methods: {
    calculate() {
      this.$emit('calculate', this.beschreibung);
    }
  }
}
</script>