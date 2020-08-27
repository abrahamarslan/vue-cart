<template>
  <div id="app">
   <Header></Header>  
   <mdb-container class="mt-5">
    <mdb-row class="justify-content-md-center align-middle">      
      <mdb-col>
        <AddProduct @addProduct="addProduct" />
      </mdb-col>
      <mdb-col>
        <ListProduct :productList="productList" />
      </mdb-col>
    </mdb-row>
   </mdb-container>
  </div>
</template>

<script>
import Header from './components/Header';
import AddProduct from './components/AddProduct';
import ListProduct from './components/ListProduct';
import { mdbContainer, mdbRow, mdbCol, mdbBtn } from "mdbvue";
import axios from 'axios';
export default {
  name: 'App',
  components: {
    mdbContainer,
    mdbRow,
    mdbCol,
    mdbBtn,
    Header,
    AddProduct,
    ListProduct
  },
  methods: {
    async getProductList() {
      try {
        let result = await axios.get('http://localhost:3000/products'); 
        this.productList = result.data
      } catch (error) {
       console.log(error) ;
      }
    },
    async addProduct(product) {
        try {
          let result = axios.post('http://localhost:3000/products', product)
          this.getProductList();
        } catch (error) {
          console.log(error);
        }
    }
  },
  data() {
    return {
      productList: []
    }
  },
  mounted() {    
    this.getProductList()
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap'); 
</style>
