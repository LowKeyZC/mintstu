<template>

</template>

<script>

  export default {
    name: 'Common',
    data () {
      return {
        arrData: [1,2,3,4,5]
      }
    },
    methods: {
      getData () {
        setTimeout(2000)
        return this.arrData
      }
    }
  }
</script>

<style scoped>

</style>
