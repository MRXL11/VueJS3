<script setup >
import {ref,reactive} from 'vue';

const courseName=ref('Frontend-Frameworks')

const student= reactive({
        name :'Bui Van Duong',
        age : 22,
        class: 'Frontend-Framework Vue JS 3',

    });
</script>
<template>
    <div id="app">
        <div class="container mb-5">
            <h1 class="display-4 mb-3">Thông tin sinh viên:</h1>

        </div>
    </div>
</template>