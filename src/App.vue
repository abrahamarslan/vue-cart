<template>
  <div id="app">
   <Header></Header>  
   <mdb-container class="mt-5">
    <mdb-row class="justify-content-md-center align-middle">      
      <mdb-col>
        <AddProduct />
      </mdb-col>
      <mdb-col>
        <ListProduct />
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
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap'); 
</style>
