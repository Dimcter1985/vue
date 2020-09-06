<template lang="pug">
  .button__wrapper
    button.button(type="button" v-on="$listeners") НАЖМИ
      //-$listeners передаем событие от родителя потомку
    slot
    button.button(type="button" @click="btnClick") НАЖМИ ЕЩЕ РАЗ
</template>

<script>
  export default {
    data() {
      return {
        
      }
    },

    methods: {
      btnClick() {
        this.$emit('clicked', 'new title')//передаем метод из потомка в родитель при помощи пользовательского события
      }
    }
  }
</script>

<style lang="scss" scoped>
  .button {
    background: blue;
    color: #ffff;
    border: none;
    padding: 5px 10px;
    border-radius: 50px;
    cursor: pointer;
    outline: none;
    margin-right: 10px;
    margin-bottom: 20px;
  }

</style>