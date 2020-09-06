<template lang="pug">
  #app
    .wrapper
      h1.title {{title}}
      inner(:items="arr" title="yes")
        div(slot-scope="{element}")
          h3 {{element}}
          hr
        h3(slot="text") hello everybody

      inp(placeholder="текст подсказка")
      btn(@click="handleClick" @clicked="changeTitle")
</template>

<script>
import inner from './components/AppInner';
import btn from './components/AppButton';
import inp from './components/AppInput';

export default {
  name: 'app',

  components: {
    inner,
    btn,
    inp
  },

  data () {
    return {
      title: 'hello world',
      arr: [1, 2, 3, 4]
    }
  },

  methods: {
    handleClick(e) {
      console.log('handleClick', e.target)
    },
    changeTitle(title) {
      this.title = title
    }
  }
}
</script>

<style lang="scss" scoped>
  .wrapper {
    background-color: red;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .title {
    font-size: 70px;
    color: gray;
  }

  .slot {
    margin-top: 20px;
  }
</style>
