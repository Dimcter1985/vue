<template lang="pug">
  .input__wrapper
    input.input(type="text" v-bind="$attrs" v-model="formData.username" value="dmitriy")
    pre {{formData}}
    //-$attrs передаем атрибут от родителя к потомку
    //-v-model передаем данные из представления в модель
</template>

<script>
  export default {
    inheritAttrs: false,

    data() {
      return {
        formData: {
          username: ''
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  .input {
    margin-bottom: 15px;
  }

</style>