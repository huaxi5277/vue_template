<template>
  <div class="hello">
    <h1>HelloWorld</h1>
    <ul>
      <li v-for="(item, index) in user" :key="index" @click="changeUser(index, $event)">
        <p>{{item.name}}</p>
        <p>{{item.age}}</p>
        <p>{{item.sex}}</p>
        
      </li>
    </ul>
  </div>
</template>

<script>
import {defineComponent} from 'vue'
export default defineComponent({
  name: 'Setup',
  props: {
    user: Object
  },
  setup(props, ctx) {
    function changeUser(index) {
      ctx.emit('change', index);
    }
    return {changeUser}
  }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  text-align: center;
}
</style>
