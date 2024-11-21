<script setup>
  import { reactive,ref,computed } from 'vue';
// Bài 1 lab3
  const product = reactive({
    id: 1,
    name: 'Sản phẩm 1',
    price: 100,
    category: 'Danh mục 1',
    quantity:20,
    inStock: true,
    imageUrl:"https://bitex.com.vn/vnt_upload/news/08_2019/Balo-mau-giao-hinh-thu-de-thuong-cho-cac-be-mam-non-02.jpg"
  });
  const listProducts=reactive([
    {
        id: 2,
        name: 'Sản phẩm 2',
        price: 200,
        category: 'Danh mục 2',
        quantity:50,
        inStock: false,
        imageUrl:"https://bitex.com.vn/vnt_upload/news/08_2019/Balo-mau-giao-hinh-thu-de-thuong-cho-cac-be-mam-non-02.jpg"
    },
    {
        id: 3,
        name: 'Sản phẩm 3',
        price: 50,
        category: 'Danh mục 3',
        quantity:5,
        inStock: true,
        imageUrl:"https://product.hstatic.net/1000238555/product/33ddd34_04b78655d040455dbb11c8f34084cbb3_compact.jpg"
    },
    {
        id: 4,
        name: 'Sản phẩm 4',
        price: 150,
        category: 'Danh mục 4',
        quantity:15,
        inStock: true,
        imageUrl:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTWBBYMCNGLlHxv38RBvz0ro7rqpW4z8zAsgQ&s"
    },
  ])

  // bài 4 lab 3
// tổng giá trị hàng tồn kho
const selectedCategory =ref('') // lọc theo danh mục
  const totalStockValue =computed(()=>{
        return listProducts.reduce((total, product)=>{
            return product.inStock ? total + product.price *product.quantity : total;
        },0)
  })
  // lọc sản phẩm theo danh mục
  const filterProducts=computed(()=>{
    if(!selectedCategory.value){
        return listProducts;
    }
    return listProducts.filter((product)=>product.category===selectedCategory.value)
  })
</script>

<template>
    <!-- bài 1 lab 3 -->
  <div class="container mt-5">
    <h5>Bài 1 Lab 3</h5>
    <div class="card mb-4 shadow-sm">
        <img :src="product.imageUrl"  class="card-img-top" alt="product image">
      <div class="card-body text-center">
        <h5 class="card-title fw-bold text-uppercase">Tên sản phẩm: {{ product.name }}</h5>
        <p class="card-text text-danger">Giá sản phẩm : ${{ product.price }}</p>
        <p class="card-text">Số lượng sản phẩm : {{ product.quantity }}</p>
        <p class="card-text">Danh mục sản phẩm : {{ product.category }}</p>
        <span class="badge"
        :class="{
            'bg-success':product.inStock,
            'bg-danger':!product.inStock,
        }"
        >
        {{ product.inStock?"Còn hàng":"Hết hàng" }}
        </span>
      </div>
    </div>
  </div>
  <div class="container">
        <!-- bài 2 lab3 -->
        <h5>Bài 2 lab 3</h5>
    <div class="card shadow-sm border">
        <img :src="product.imageUrl"  class="card-img-top" alt="product image">
      <div class="card-body text-center">
        <h5 class="card-title">Tên sản phẩm: {{ product.name }}</h5>
        <p class="card-text">Giá sản phẩm : ${{ product.price }}</p>
        <p v-if="product.quantity >10" class="text-success">Số lượng lớn</p>
        <p v-else-if="product.quantity >0" class="text-warning">Số lượng vừa </p>
        <p v-else class="text-danger">Hết hanf </p>
        <p class="card-text">Danh mục sản phẩm : {{ product.category }}</p>
        <span class="badge"
        :class="{
            'bg-success':product.inStock,
            'bg-danger':!product.inStock,
        }"
        >
        {{ product.inStock?"Còn hàng":"Hết hàng" }}
        </span>
      </div>
    </div>
  </div> 
 <!-- bài 3 lab 3 -->
  <div class="container">
    <h5>Bài 3 lab 3</h5>
    <table class="table table-hover table-bordered">
        <thead>
            <tr>
                <th scope="col">#</th>
                <th scope="col">Ảnh</th>
                <th scope="col">Tên</th>
                <th scope="col">Giá</th>
                <th scope="col">Tình trạng</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="({ id,name,price,inStock,imageUrl },index) in listProducts" :key="id">
                <th scope="row">{{ index+1 }}</th>
                <td text-center><img :src="imageUrl" alt="Product Image" width="50" height="50"/></td>
                <td>{{ name }}</td>
                <td>{{ price }} VND</td>
                <td text-center>
                    <span v-if="inStock" class="badge bg-success">Còn hàng</span>
                    <span v-else class="badge bg-danger">Hết hàng</span>
                </td>
            </tr>
        </tbody>
    </table>
  </div>

  <!-- bài 4 lab 3 -->
  <div class="container">
    <h5>Bài 4 lab 3</h5>
    <h2>Quản lý sản phẩm</h2>
    <div class=" ">
        <label for="categoryFilter">Lọc theo danh mục</label>
        <select v-model="selectedCategory" class="form-select" id="categoryFilter">
            <option value="">Tất cả</option>
            <option value="Danh mục 2">Danh mục 2</option>
            <option value="Danh mục 3">Danh mục 3</option>
            <option value="Danh mục 4">Danh mục 4</option>
        </select>
    </div>
    <!-- tổng hàng trong kho -->
     <div class="alert alert-info">Tổng giá trị hàng tồn kho : {{ totalStockValue }} VND</div>
     <!-- danh sách sản phẩm -->
      <div class="row">
        <template 
        v-for="product in filterProducts"
        :key="product.id"
        class="product-template"
        >
        <div class="col-md-4">
          <div class="card shadow-sm">
            <img :src="product.imageUrl" class="card-img-top" alt="Produtc Image">
            <div class="card-body">
              <h5 class="card-title badge bg-primary">{{ product.name }}-{{ product.category }}</h5>
              <p v-if="product.inStock" class="text-success">Còn hàng</p>
              <p v-else class="text-danger">Hết hàng</p>
              <p>Giá: {{ product.price }} VND</p>

            </div>
          </div>
        </div>
        </template>
      </div>
  </div>
</template>
