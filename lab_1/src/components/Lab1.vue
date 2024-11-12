<script setup >
import {ref,reactive} from 'vue';

const students= reactive([{
        name :'Bui Van Duong',
        age : 22,
        class: 'Frontend-Framework Vue JS 3',

    },
    {
        name :'Bui Van Khánh',
        age : 20,
        class: 'Frontend-Framework Vue JS 2',
    },
    {
        name :'Bui Van Ngọc',
        age : 21,
        class: 'Frontend-Framework Vue JS 1',
    },
    ]);
</script>
<template>
<div class="container mt-5">
   <form action="" class="p-4 border rounded bg-light">
    <div class="d-flex mb-3 justify-content-between align-items-center">
        <h1>Danh sách sinh viên</h1>
        <button class="btn btn-success btn-lg">Thêm mới</button>
    </div>
    <table class="table table-striped table-bordered" >
        <thead class="thead-dark fw-bold">
            <tr>
                <th scope="col" >STT</th>
                <th scope="col">Họ và tên</th>
                <th scope="col">Tuổi</th>
                <th scope="col">Lớp học</th>
                <th scope="col">Chức năng</th>
            </tr>
        </thead>
        <tbody class="table-group-divider">
            <!-- cái ni giống vòng lặp for -->
            <tr v-for="(student,index) in students" :key="index">   
                <td>{{ index+1 }}</td>
                <td>{{ student.name }}</td>
                <td>{{ student.age }}</td>
                <td>{{ student.class }}</td>
                <td>
                    <button class="btn btn-warning btn-sm ms-2">Sửa</button>
                    <button class="btn btn-danger btn-sm ms-2">Xóa</button>
                </td>
            </tr>

        </tbody>
    </table>
   </form>
</div>
</template>