<template>
  <div class="text-center">
    <input class="w-75" type="text" v-on:keydown.enter="onInput">
    <!-- <input class="w-75" type="text" v-on:input="onInput"> -->
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
    onInput(e){
      // 'inputChange'는 부모 객체에서 부를 이름
      this.$emit('inputChange', e.target.value)
    }
  }
}
</script>

<style>

</style>