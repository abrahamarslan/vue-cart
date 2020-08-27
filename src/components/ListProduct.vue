<template>
 <mdb-container>
    <mdb-row>
      <mdb-col size="12" class="text-center mb-5">
        <mdb-btn type="button" @click.native="showModal = true" color="info">Show Product List</mdb-btn>
        <mdb-modal :show="showModal" @close="showModal = false" size="fluid" cascade class="text-left">
          <mdb-modal-header class="primary-color white-text">
            <h4 class="title"><span class="fa fas fa-list" /> Product List</h4>
          </mdb-modal-header>
          <mdb-modal-body class="grey-text">
            <mdb-tbl responsive>
                <mdb-tbl-head color="primary-color" textWhite>
                    <tr>
                    <th>#</th>
                    <th>Name</th>
                    <th>Brand</th>
                    <th>Price</th>
                    <th>Availability</th>
                    <th>Action</th>                
                    </tr>
                </mdb-tbl-head>
                <mdb-tbl-body>
                    <tr scope="row" v-for="(product, index) in productList" :key="index">
                        <th scope="row">{{index+1}}</th>
                        <td>{{product.name}}</td>
                        <td>{{product.brand}}</td>
                        <td>${{product.price}}</td>
                        <td>
                            <mdb-badge color="success" v-if="product.inventoryStatus==='true'">In Stock</mdb-badge>
                            <mdb-badge color="danger" v-else>Out of Stock</mdb-badge>
                        </td>
                        <td>
                            <updateProduct :product="product" @updateProduct="updateProduct" @deleteProduct="deleteProduct"></updateProduct>
                        </td>                    
                    </tr>                   
                </mdb-tbl-body>
                </mdb-tbl>
          </mdb-modal-body>
          <mdb-modal-footer>
            <mdb-btn color="secondary" @click.native="showModal = false">Close</mdb-btn>
          </mdb-modal-footer>
        </mdb-modal>
      </mdb-col>
    </mdb-row>
  </mdb-container>
</template>

<script>
import { mdbContainer, mdbRow, mdbCol, mdbInput, mdbTextarea, mdbBtn, mdbIcon, mdbModal, mdbModalHeader, mdbModalBody, mdbModalFooter, mdbTbl, mdbTblHead, mdbTblBody } from 'mdbvue';
import UpdateProduct from './UpdateProduct';
import axios from 'axios';

export default {
    name: 'ListProduct',
    components: {
      mdbContainer,
      mdbRow,
      mdbCol,
      mdbInput,
      mdbTextarea,
      mdbBtn,
      mdbIcon,
      mdbModal,
      mdbModalHeader,
      mdbModalBody,
      mdbModalFooter,
      mdbTbl,
      mdbTblHead,
      mdbTblBody,
      UpdateProduct
    },
    props: ['productList'],
    data() {
      return {
        showModal: false
      };
    },
    methods: {
      async updateProduct(product) {
        try {
          let result = await axios.put('http://localhost:3000/products/'+product.id, product)          
        } catch (error) {
          console.log(error);
        }
      },
      async deleteProduct(product) {
        console.log(product);
        try {
          let result = await axios.delete('http://localhost:3000/products/'+product.id)          
        } catch (error) {
          console.log(error);
        }
      }
    }
}
</script>

<style>

</style>