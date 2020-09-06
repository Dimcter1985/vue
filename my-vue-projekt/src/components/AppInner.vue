<template lang="pug">
  .inner-wrapper
    h2.title {{title}}
    h3.subtitle {{subtitle}}
    p.text Высококачественный прототип будущего проекта говорит о возможностях поставленных обществом задач. Но непосредственные участники технического прогресса призывают нас к новым свершениям, которые, в свою очередь, должны быть описаны максимально подробно! Внедрение современных методик позволяет оценить значение дальнейших направлений развития.
    slot(name="text") 
    //-именнованый слот
    ul
      li(v-for="item in items")
        slot(:element="item")
</template>

<script>
  import testMixin from "../mixins/testMixin.js";

  export default {
    props: {
      items: Array,
      title: {
        type: String,
        default:'Hello user!',
        validator(value) {
          return ['yes', 'no'].indexOf(value) != -1//валидация передоваемых свойств
        }
      }
    },

    mixins: [testMixin],// примеси

    data() {
      return {
        
      }
    },
    //хуки жизненного цикла Vue
    beforeCreate() {//при создании экземпляра Vue. DOM недоступен, данные не реактивныю
      console.log('beforeCreate');
    },
    created() {//данные уже реактивны, доступны методы вотчеры и события но функция рендер еще не запущена
      console.log('created');
    },
    beforeMount() {//мало чем отличается от created
      console.log('beforeMount');
    },
    mounted() {//компонент полностью готов к работе
      console.log('mounted');
    },
    beforeUpdate() {//обновление компонента
      console.log('beforeUpdate');
    },
    updated() {//компонент обновлен
      console.log('updated');
    },
    beforeDestroy() {//копонент еще функционален
      console.log('beforeDestroy');
    },
    destroyed() {//компонент изьят из дом дерева
      console.log('destroyed');
    }


  }
</script>

<style lang="scss" scoped>
  .title {
    font-size: 40px;
    color: purple;
  }

</style>