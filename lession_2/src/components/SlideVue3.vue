<!-- <script setup >
import { reactive , ref } from 'vue';
const students=[{
    name: "Bùi Văn Dương",
    point: 9,
},
{
    name: "Nguyễn Văn A",
    point: 4,
},
]
</script>

<template>
    <div class="container">
        <h3>V-IF / V-ELSE</h3>
        <div v-for="(student, index) in students" :key="index" class="mt-4">
        <div v-if="student.point >=5" class="alert alert-success mt-4">
            {{ student.name }} qua môn
        </div>
        <div v-else class="alert alert-danger">
            {{ student.name }} không qua môn
        </div>
    </div>
</div>
</template> -->

<!-- Tạo form đăng nhập, true thì đăng nhập còn ngược lại thì báo không được cấp quyền -->

<!-- <script setup >
    import { reactive, ref } from 'vue';
    const isLogin=ref(true
        
    );
    const username=ref('Dương');

</script>
<template>
<div class="container mt-5">
    <div v-if="!isLogin" role="alert" class="login-form">
       <h2> Đăng nhập</h2>
        <input type="text" class="form form-control mb-2" placeholder="Tên đăng nhập">
        <input type="text" class="form form-control" placeholder="Mật khẩu">
        <button class="btn btn-primary">Đăng nhập</button>
</div>
<div v-if="isLogin" class="alert alert-success mt-4" role="alert">Xin chào {{ username }} ! Bạn đã đăng nhập thành công</div>
</div>
</template> -->

 <!-- //>=9.0 xuất sắc 
 8-8.9 giỏi
 6.5-7.9 khá
 5-6.4 trung bình
 5 yếu -->
<!-- <script setup>
import {ref} from 'vue';
    const diem= ref(9)
</script>
<template>
    
<div class="container">
    <h3>V-IF / V-ELSEIF / V-ELSE</h3>
    <div v-if="diem >= 9" class="alert alert-success mt-4">
        Xin chúc mừng bạn đã đạt điểm: {{ diem }} - Xuất sắc
    </div>
    <div v-else-if="diem >= 8" class="alert alert-info mt-4">
        Bạn đã đạt điểm: {{ diem }} - Giỏi
    </div>
    <div v-else-if="diem >= 6.5" class="alert alert-warning mt-4">
        Bạn đã đạt điểm: {{ diem }} - Khá
    </div>
    <div v-else-if="diem >= 5 " class="alert alert-dark mt-4">
        Bạn đã đạt điểm: {{ diem }} - Trung bình
    </div>
    <div v-else class="alert alert-danger mt-4">
        Bạn đã đạt điểm: {{ diem }} - Yếu
    </div>
    
</div>
</template> -->
<!-- V-show -->
<!-- <script setup >
import {ref} from 'vue';
// khai báo trạng thái
const isAbsent = ref(true);
// khai báo thêm 1 hàm đổi trạng thái
const toggleAbsent =()=>{
    isAbsent.value = !isAbsent.value;
}
</script>
<template>
    <h1>V-Show</h1>
    <div class="container mt-4" >
        <button @click="toggleAbsent" :class="isAbsent ?'btn btn-danger mb-3':'btn btn-primary mb-3'">
            {{ isAbsent ? 'Vắng mặt': 'Có mặt'}}
        </button>
        Thông báo hiển thị nếu true thì vắng mặt còn false thì có mặt -->
         <!-- <div v-show="isAbsent" class="alert alert-warning" role="alert">Vắng mặt</div>
         <div v-show="!isAbsent" class="alert alert-success" role="alert">Có mặt</div>
    </div>
</template> -->

<!-- V-for -->

<script setup>
import {reactive,ref} from 'vue';
// const listFood=reactive(['Pizza', 'Burger','Bún Bò','Cơm rang']);
    // const des_food=reactive({
    //     pizza:20,burger:30,shushi:40
    // })
    const listFood=reactive([
        {
            id: '01',
            name: 'pizza',
            quantity:0,
            price:20,
        },
        {
            id: '02',
            name: 'burger',
            quantity:0,
            price:50,
        },
        {
            id: '03',
            name: 'bún bò',
            quantity:0,
            price:80,
        }
    ])
    // hàm tính tiền
    function totalMoney(){
        return listFood.reduce((total,item)=>{
            return total +item.price *item.quantity;
        },0).toFixed(2);
    }
    // hàm tăng số lượng
    function increaseQuantity(index){
        listFood[index].quantity++;
    }
    // hàm giảm số lượng
    function decreaseQuantity(index){
        if(listFood[index].quantity > 0){
            listFood[index].quantity--;
        }

    }
</script>
<template>
    <!-- <h1>Danh sách món ăn hôm nay V-FOR</h1>
    <div class="container mb-3 list-group" >
        <ul v-for="(food,index) in listFood" :key="index" class=" list-group-item">
            <li>{{ index+1 }}.{{ food }}</li>
        </ul>
    </div> -->
    <!-- in danh sách với đối tượng -->
<!-- <div class="container">
    <p>Danh sách món làm việc với đối tượng</p>
     <ul v-for="(price,food,index) in des_food" :key="index">
        <li>{{ index+1 }}- {{ food }}- giá: {{ price }}$</li>
     </ul>
</div> -->

<!-- áp dụng với giỏ hàng -->
 <div class="container">
    <p>Giỏ hàng</p>
    <table class="table table-bordered">
        <thead>
            <tr>
                <th>ID</th>
                <th>Tên</th>
                <th>Giá</th>
                <th>Số lượng</th>
                <th>Số tiền</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(food,index) in listFood" :key="food.id">
                <td>{{ food.id }}</td>
                <td>{{ food.name }}</td>
                <td>{{ food.price }}</td>
                <td>
                    <button type="submit" class="btn" @click="decreaseQuantity(index)">-</button>
                    <input type="text" class="form-control" v-model="food.quantity">
                    <button type="submit" class="btn" @click="increaseQuantity(index)">+</button>
                </td>
                <td>{{ (food.quantity *food.price).toFixed(2) }}</td>
            </tr>
        </tbody>
    </table>
    <h2>Tổng tiền : {{ totalMoney() }} $</h2>
 </div>
</template>