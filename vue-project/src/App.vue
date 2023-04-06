<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Welcome from './components/Welcome.vue'
import { ref } from 'vue';

const listUser = [
  {
    name: 'Manh',
    age: 24
  },
  {
    name: 'Duc',
    age: 24
  },
  {
    name: 'An',
    age: 24
  },
]
const hideSlot = ref(true)
const showAll = ref(true)
function changeAll(){
  showAll.value = !showAll.value
}
</script>

<template>
    <div class="container" style="display: flex; justify-content: space-around; width: 100%; flex-wrap: wrap;">
      <HelloWorld :listUser="listUser" @hide-all="changeAll" v-if="showAll"/>
      <button v-if="!showAll" @click="changeAll()">Hiện tất cả</button>
    </div>
    <div>
      <Welcome>
        <button v-if ="hideSlot" @click="hideSlot = false">Ẩn để thay slot mặc định</button>
        <template v-slot:footer>
          <button>Nội dung truyền cho slot footer name</button>
        </template>
      </Welcome>
    </div>
</template>

<style scoped>

</style>
