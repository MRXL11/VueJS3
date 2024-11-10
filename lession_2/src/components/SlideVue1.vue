<script setup >
const name ="Font-end Framework Vue JS 3"
const time ="30 hours"
const active ="true"
</script>
<template>
    <div class="container mt-5">
        <h1 class="display-4 mb-3">Thông tin khóa học</h1>
        <ul class="list-group">
            <li class="list-group-item">Tên khóa học : {{ name }}</li>
            <li class="list-group-item">Giờ học : {{ time }}</li>
            <li class="list-group-item">Trạng thái : {{ active?"Mở":"Đóng" }}</li>
        </ul>
    </div>
</template>