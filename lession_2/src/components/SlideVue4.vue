<script setup>
 // =============================================================================================event binding: sự kiện 
//  // inline handler: Cho phép định nghĩa các hàm xử lý sự kiện trực tiếp trong html(templates)
// import {ref} from 'vue';
// // const counter=ref(0);
// // const counter1= ref(0);
// // // method handler: trong các bài toán thực tế thì mã xử lý sự kiện không chì dừng lại ở một lệnh đơn giản
// // // Khi mà logic phức tạp hơn thì vue cho phép tách phần tử xử lý sự kiện vào các hàm (method), giúp cho mã dễ đọc và bảo trì
// // const increament=()=>{
// //     counter1.value++;
// // }
// // ví dụ về tăng số
// // // tạo 2 nút, 1 nút bấm tăng 2 lần 1 nút tăng 5 lần
// // const counterx=ref(0);

// // hàm nhận vào tham số
// // const increamentx=(amount)=>{
// //     counterx.value+=amount;
// // }
// const counter=ref(0);
// const increment=()=>{
//     counter.value++;
// }
// const decrement=()=>{
//     counter.value--;
// }
// const reset=()=>{
//     counter.value=0;
// }
// =========================================================================event modifier==
// .stop: ngăn chặn sự kiện không tiếp tục truyền lên các phần tử cha trong DOM
// .prenevent: sử dụng để ngăn chặn hành vi mặc định của sự kiện
// .capture: dùng để lắng nghe sự kiện 
// .self : Chỉ kích hoạt sự kiện với chính phần tử đang gán sự kiện
// .once : chỉ kích hoạt sự kiện 1 lần


// ví dụ về .prenevent
// function formHandler(event){
//     console.log('Form đã được gửi');
// }

// key modiflier
// const submitForm=()=>{
//     console.log('Form đã được gửi')
// }

//============================================================================================ PHẦN 2: FORM BINDING
// text :input
// import {ref} from 'vue';

// // const message=ref("")
// // const feedback= ref("");
// // const isCheck=ref(false);
// // const courseName=ref([]);
// // radio
// const chooseMajor=ref(["js"]);
import {ref} from 'vue'
const selectLanguage=ref("");
</script>;
<template>

 <!-- <button class="btn btn-success" @click="increament()">
    Số lần bấm counter : {{ counter1 }}
 </button> 
 <button class="btn btn-primary" @click="counter++">
    Số lần bấm counter : {{ counter }}
 </button>
 <button class="btn btn-dark" @click="increamentx(2)">
    Tăng 2 lần
 </button> <br>
 <button class="btn btn-dark" @click="increamentx(5)">
    Tăng 5 lần
 </button> <br>
 <p>Số lần bấm : {{ counterx }}</p> -->
 <!-- <span><button class="btn btn-success" @click="increment()">Tăng </button>
 <p>{{ counter }}</p>
 <button class="btn btn-success" @click="decrement()">Giảm </button> </span>
 <button class="btn btn-success" @click="reset()">Đặt lại</button> -->
<!-- event modiflier -->
 <!-- <form action="" @submit.prevent="formHandler()">
    <button type="submit">Gửi</button>
 </form> -->
<!-- 
 key modiflier -->
 <!-- các key modiflier -->
  <!-- nút enter, nút tab,nút delete, nút esc, nút space, nút up, nút down. -->
 <!-- <input type="text" placeholder="Nhấn enter để gửi" @keyup.enter="submitForm()"> -->
<!-- ===============================================================================Phần 2 : form binding -->
 <!-- text input -->
  <!-- <input type="text" v-model="message" placeholder="Nhập vào đây">
  <p>Thứ bạn đã nhập : {{message }}</p> -->
  <!-- multi line text  -->
 <!-- <span>Để lại góp ý ở đây</span>
 <textarea v-model="feedback" placeholder="Góp ý" ></textarea>
 <p>Góp ý của bạn{{ feedback }}</p>
<label for="">
    <input type="checkbox" v-model="isCheck" />Chấp nhận điều khoản
</label>
<p>Trạng thái: {{ isCheck ? "Chấp nhận":"Không chấp nhận" }}</p> -->
<!-- <label for="">
    <input type="checkbox" v-model="courseName" value="HTML5"/>HTML5 <br>
    <input type="checkbox" v-model="courseName" value="JS"/>JS <br>
    <input type="checkbox" v-model="courseName" value="VUE"/>VUE <br>
    <input type="checkbox" v-model="courseName" value="PHP"/>PHP <br>
<p>Bạn đã chọn khóa học: {{ courseName }} </p>
</label> -->
<!-- <p>Lựa chọn ngành học : </p>
    <input type="radio" id="js" value="js" v-model="chooseMajor"/>
    <label for="red">JS</label>
    <input type="radio" id="vue" value="vue" v-model="chooseMajor"/>
    <label for="vue">Vue</label>
    <p>Lựa chọn của bạn {{ chooseMajor }}</p> -->



    <!-- Select option  -->

    
  </template>