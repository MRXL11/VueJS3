<!-- <script setup>
import { ref } from 'vue';
const count = ref(0)
function increment() {
    count.value++;
}
</script>
<template>
    <h1>Exam App</h1> <br>
    <p>Tăng số lượng: {{ count }}</p> <br>
    <button @click="increment"> Tăng số </button>
</template> -->

 <!-- 2 cách đề viết API -->
<!-- Option API -->

<!-- <script >
    export default {
        data() {
            return {
                counter: 0
            }
        },
        methods: {
            increnmentCounter(){
                this.counter++;
            }
        }
    };
</script>
<template>
    <div id="app">
    <h1>Exam App</h1> <br>
    <p>Tăng số lượng: {{ counter }}</p> <br>
    <button @click="increnmentCounter"> Tăng số </button>
    </div>
</template> -->

<!-- Composition API (chủ yếu dùng cái này) --> 
 <!-- <script setup >
 import {ref} from 'vue';
 const count = ref(0);

 // định nghĩa hàm tăng giá trị của count lên 1
 const increnmentCounter= ()=>{                      // đây là hàm.
    count.value++; // tăng giá trị count lên 1
 }
</script>
<template>
    <div id="app">
    <h1>Exam App</h1> <br>
    <p>Tăng số lượng: {{ count }}</p> <br>
    <button @click="increnmentCounter"> Tăng số </button>
    </div>
</template> -->


<!-- <script setup >
    import {ref}  from 'vue' 
    // Khai báo các trạng thái sử dụng ref
    const name= ref('Frontend -framework Vue JS3')
    const time=ref(30)
    const level=ref('Nâng cao')
    const active=ref(true)
</script>
<template>
    <div id="app">
        <div class="container mb-5">
            <h1 class="display-4 mb-3">Thông tin khóa học:</h1>
            <ul class="list-group">
                <li class="list-group-item">Tên khóa học: {{ name }}</li>
                <li class="list-group-item">Thời gian: {{ time }} giờ</li>
                <li class="list-group-item">Trình độ: {{ level }}</li>
                <li class="list-group-item">Trạng thái: {{ active ? 'Mở': 'Đóng' }}</li>
            </ul>
        </div>
    </div>
</template> -->

<!-- Reactive: làm việc với mảng và đối tượng --> 
 <!-- <script setup>
    import { reactive } from 'vue';
    
    const student=reactive({
        name :'Bui Van Duong',
        age : 22,
        class: 'Frontend-Framework Vue JS 3',

    });

    // const printInfo = () => {
    //     state.counter++;
    // }
</script>
<template>
    <div id="app">
        <div class="container mb-5">
            <h1 class="display-4 mb-3">Thông tin khóa học:</h1>
            <ul class="list-group">
                <li class="list-group-item">Tên sinh viên: {{ student.name }}</li>
                <li class="list-group-item">Tuổi: {{ student.age }} tuổi</li>
                <li class="list-group-item">Lớp: {{ student.class }}</li>
            </ul>
        </div>
    </div>
</template> -->

<!-- hỗn hợp -->

<!-- <script setup >
import {ref,reactive} from 'vue';
// khai báo trạng thái với ref: sử dụng kiểu dữ liệu nguyên thủy
const courseName=ref('Frontend-Frameworks')
// Khai báo trạng thái với reactive
const student= reactive({
        name :'Bui Van Duong',
        age : 22,
        class: 'Frontend-Framework Vue JS 3',

    });
</script>
<template>
    <div id="app">
        <div class="container mb-5">
            <h1 class="display-4 mb-3">Thông tin khóa học:</h1>
            <ul class="list-group">
                <li class="list-group-item">Tên sinh viên: {{ student.name }}</li>
                <li class="list-group-item">Tuổi: {{ student.age }} tuổi</li>
                <li class="list-group-item">Lớp: {{ student.class }}</li>
                <li class="list-group-item">Tên khóa học: {{ courseName }}</li>
            </ul>
        </div>
    </div>
</template> -->

<!-- Các chỉ thị và ràng buộc -->
 <!-- ràng buộc thuộc tính SRC -->
<!-- <script setup >
import {ref,reactive} from 'vue';
// khai báo trạng thái với ref: sử dụng kiểu dữ liệu nguyên thủy
const courseName=ref('Frontend-Frameworks')
// Khai báo trạng thái với reactive
const student= reactive({
        name :'Bui Van Duong',
        age : 22,
        class: 'Frontend-Framework Vue JS 3',
        avatar: '/ronaldo.jfif'
        // đường dẫn ảnh trực tiếp trong thư mục
    });
</script>
<template>
    <div id="app">
        <div class="container mb-5">
            <h1 class="display-4 mb-3">Thông tin sinh viên:</h1>
            <div class="card">
                <img 
                :src="student.avatar"
                class="card-img-top w-50 mx-auto"
                alt="{{ studen.name }}"
                >
            </div>
            <ul class="list-group">
                <li class="list-group-item">Tên sinh viên: {{ student.name }}</li>
                <li class="list-group-item">Tuổi: {{ student.age }} tuổi</li>
                <li class="list-group-item">Lớp: {{ student.class }}</li>
                <li class="list-group-item">Tên khóa học: {{ courseName }}</li>
            </ul>
        </div>
    </div>
</template> -->

<!-- click đổi tên -->
<!-- <script setup >
import {ref} from 'vue';

const myName=ref('Bùi Văn Dương')
function changeName(){
    myName.value='Bùi Duy Khánh';
}
</script>
<template>
    <div class="container">
        <h1>Hello, {{ myName }}</h1>
        <button @click="changeName" class="btn btn-success">Đổi tên</button>
    </div>
</template> -->

<!-- Đồng bộ 2 chiều -->

<script setup >
import {ref} from 'vue'
const myName=ref('Nguyễn Văn D')
</script>
<template>
    {{ myName }}
    <input type="text" v-model="myName"/>
</template>


