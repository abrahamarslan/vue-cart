<template>
 <mdb-container>
    <mdb-row>
      <mdb-col size="12" class="text-center mb-5">
        <mdb-btn type="button" @click.native="showModal = true" color="info">Show Product List</mdb-btn>
        <mdb-modal :show="showModal" @close="showModal = false" cascade class="text-left">
          <mdb-modal-header class="primary-color white-text">
            <h4 class="title"><fa class="fas fa-list" /> Product List</h4>
          </mdb-modal-header>
          <mdb-modal-body class="grey-text">
            <mdb-tbl responsive>
                <mdb-tbl-head color="primary-color" textWhite>
                    <tr>
                    <th>#</th>
                    <th>Name</th>
                    <th>Type</th>
                    <th>Price</th>
                    <th>Action</th>                
                    </tr>
                </mdb-tbl-head>
                <mdb-tbl-body>
                    <tr scope="row">
                        <th scope="row">1</th>
                        <td>Cell</td>
                        <td>Cell</td>
                        <td>Cell</td>
                        <td>Cell</td>                    
                    </tr>
                    <tr scope="row">
                        <th scope="row">2</th>
                        <td>Cell</td>
                        <td>Cell</td>
                        <td>Cell</td>
                        <td>Cell</td>                    
                    </tr>
                    <tr scope="row">
                        <th scope="row">3</th>
                        <td>Cell</td>
                        <td>Cell</td>
                        <td>Cell</td>
                        <td>Cell</td>                    
                    </tr>
                    <tr scope="row">
                        <th scope="row">4</th>
                        <td>Cell</td>
                        <td>Cell</td>
                        <td>Cell</td>
                        <td>Cell</td>                    
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
      mdbTblBody
    },
    data() {
      return {
        showModal: false
      };
    }
}
</script>

<style>

</style>