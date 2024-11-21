<script setup>
    import { ref } from 'vue';
    const bookTitle = ref('');
    const bookAuthor = ref('');
    const bookCategory = ref('');
    const bookQuantity = ref(1);
    const books = ref([]);
    const isEditing = ref(false);
    const editingBookId = ref(null);
    const categories = {
        1: "Tiểu thuyết",
        2: "Hư cấu",
        3: "Khoa học",
        4: "Lịch sử",
        5: "Xã hội và Nhân văn",
    };

    const addBook = () => {
        if (!bookTitle.value || !bookAuthor.value || !bookCategory.value || !bookQuantity.value) {
            return;
        }

        if (isEditing.value) {
            const bookIndex = books.value.findIndex((book) => book.id === editingBookId.value);
            if (bookIndex !== -1) {
                books.value[bookIndex] = {
                    id: editingBookId.value,
                    title: bookTitle.value,
                    author: bookAuthor.value,
                    category: categories[bookCategory.value],
                    quantity: bookQuantity.value,
                };
            }
            clearForm();
        } else {
            const newBook = {
                id: Date.now(),
                title: bookTitle.value,
                author: bookAuthor.value,
                category: categories[bookCategory.value],
                quantity: bookQuantity.value,
            };
            books.value.push(newBook);
            clearForm();
        }
    };

    const deleteBook = (id) => {
        if (confirm("Bạn có muốn xóa không?")) {
            books.value = books.value.filter((book) => book.id !== id);
        }
    };

    const editBook = (book) => {
        bookTitle.value = book.title;
        bookAuthor.value = book.author;
        bookCategory.value = Object.keys(categories).find((key) => categories[key] === book.category);
        bookQuantity.value = book.quantity;
        isEditing.value = true;
        editingBookId.value = book.id;
    };

    const clearForm = () => {
        bookTitle.value = '';
        bookAuthor.value = '';
        bookCategory.value = '';
        bookQuantity.value = 1;
        isEditing.value = false;
        editingBookId.value = null;
    };
</script>

<template>
    <div class="container">
        <h1>Lab 4</h1>
        <h2>{{ isEditing.value ? 'Chỉnh sửa sách' : 'Thêm mới' }}</h2>
        <form @submit.prevent="addBook">
            <div class="mb-3">
                <label for="bookTitle" class="form-label">Tiêu đề</label>
                <input type="text" v-model="bookTitle" class="form-control" id="bookTitle" placeholder="Nhập tiêu đề" />
            </div>
            <div class="mb-3">
                <label for="bookAuthor" class="form-label">Tác giả</label>
                <input type="text" v-model="bookAuthor" class="form-control" id="bookAuthor" placeholder="Nhập tác giả" />
            </div>
            <div class="mb-3">
                <label for="bookCategory" class="form-label">Thể loại</label>
                <select v-model="bookCategory" id="bookCategory" class="form-select">
                    <option value="" disabled>Chọn thể loại</option>
                    <option value="1">Tiểu thuyết</option>
                    <option value="2">Hư cấu</option>
                    <option value="3">Khoa học</option>
                    <option value="4">Lịch sử</option>
                    <option value="5">Xã hội và Nhân văn</option>
                </select>
            </div>
            <div class="mb-3">
                <label for="bookQuantity" class="form-label">Số lượng</label>
                <input type="number" v-model="bookQuantity" class="form-control" id="bookQuantity" placeholder="Nhập số lượng" min="1" />
            </div>
            <button type="submit" class="btn btn-primary">{{ isEditing ? "Cập nhật sách" : "Thêm sách" }}</button>
        </form>
        <div v-if="books.length" class="mt-4">
            <h3>Danh sách Sách</h3>
            <ul class="list-group">
                <li v-for="book in books" :key="book.id" class="list-group-item d-flex justify-content-between align-items-center">
                    <div>
                        <h5>{{ book.title }}</h5>
                        <p>Tác giả: {{ book.author }}</p>
                        <p>Thể loại: {{ book.category }}</p>
                        <p>Số lượng: {{ book.quantity }}</p>
                    </div>
                    <div>
                        <button @click="deleteBook(book.id)" class="btn btn-danger">Xóa</button>
                        <button @click="editBook(book)" class="btn btn-warning me-2">Sửa</button>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>
