<template>
  <div class="home">
    {{name}}
    {{student.name}}
    <button @click="changeName">测试监听</button>
    <Setup :user="user" @change="changeUser"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Setup from '@/components/setup.vue'
import {ref, defineComponent, reactive, watch} from 'vue'
export default defineComponent({
  name: 'Home',
  components: {
    Setup
  },
  setup() {
    const name = ref('huaxi');
    const student = reactive({
      name: 'huaxi',
      age: 13
    })
    const user = reactive([
      {
      name: 'huaxi',
      age: 13,
      sex: '男'
    },
    {
      name: 'xiaobo',
      age: 16,
      sex: '女'
    },
    ])
    watch([name, () => student.name], (newValue, oldValue)=> {
      console.log(newValue)
      console.log(oldValue)
    })
    function changeUser(index) {
      user[index].name = 'gouzi';
    }
    function changeName() {
      student.name = '111'
    }
    return {name, user, student, changeName, changeUser}
  }
})
</script>
