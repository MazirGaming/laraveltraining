<script setup>
import { reactive, ref, defineProps } from 'vue';

const props = defineProps({
  listUser: Array
})
const isRed = ref(false);
const style = reactive({
  activeColor: 'green',
  fontSize: 30
})

const model = reactive({
  textInput: '',
  checked: false,
})

</script>

<template>
  <div style="display: flex; flex-direction: column; align-items: center; border: 1px solid black; width: 33%;">
    <h3 :class="{color: isRed}">Welcome to Mazir Gaming</h3>
    <button  @click="isRed = !isRed">Ấn vào tôi để đổi màu</button>
    <h3 :style="{ color: style.activeColor, fontSize: style.fontSize + 'px' }">
      Binding Style with color: {{ style.activeColor }} and fontSize: {{ style.fontSize }}
    </h3>
  </div>
  <div style="display: flex; flex-direction: column; align-items: center; border: 1px solid black; width: 33%;">
    <input style="margin-top: 10px;" v-model="model.textInput" placeholder="Nhập vào đây">
    <h3>Sử dụng v-model cho input có thể theo dõi được sự thay đổi dữ liệu</h3>
    <h3 style="color: red;">Nhập thử đi, sẽ hiện ở đây này: {{ model.textInput }}</h3>

    <input type="checkbox" id="checkbox" v-model="model.checked" />
	  <label for="checkbox">Kiểm tra giá trị checkbox :{{ model.checked }}</label>
  </div>
  <div style="display: flex; flex-direction: column; align-items: center; border: 1px solid black; width: 33%;">
    <h1>Hãy thử truyền emit khi dùng sự kiện ở Component con</h1>
    <button  @click="$emit('hide-all')">Ẩn tất cả</button>
  </div>
  <div style="display: flex; flex-direction: column; align-items: center; border: 1px solid black; width: 33%; margin-top: 15px;">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Name</th>
          <th scope="col">Age</th>
        </tr>
      </thead>
      <tbody>
        <template v-for="(user, index) in props.listUser">
          <tr>
            <th scope="row">{{ index }}</th>
            <td>{{ user.name }}</td>
            <td>{{ user.age }}</td>
          </tr>
        </template>
        </tbody>
      </table>
    </div>
</template>

<style scoped>
.color{
  color: red;
}
</style>
