<template>
 <mdb-container>
    <mdb-row>
            <form @submit.prevent="onSubmit">
                <mdb-col size="12" class="text-center mb-5">
                    <mdb-btn @click.native="showModal = true" type="button" color="info">Add New Product</mdb-btn>
                    <mdb-modal :show="showModal" @close="showModal = false" cascade class="text-left">
                    <mdb-modal-header class="primary-color white-text">
                        <h4 class="title"><span class="fa fas fa-pencil-alt" /> Add New Product</h4>
                    </mdb-modal-header>
                    <mdb-modal-body class="grey-text">
                        <mdb-input v-validate="{required: true, min: 3}" size="sm" v-model="form.name" name="name" label=" Product name" icon="file-signature" group type="text" validate error="wrong" success="right" trim/>                                                    
                        <small class="form-text text-muted red-text" v-show="submitted">
                            {{ errors.first('name') }}
                        </small>

                        <mdb-input size="sm" v-validate="{required: true, numeric: true}" v-model="form.price" name="price" label="  Product price" icon="money-bill" group type="text" validate error="wrong" success="right" trim/>
                        <small class="form-text text-muted red-text" v-show="submitted">
                            {{ errors.first('price') }}
                        </small>
                        <mdb-input size="sm" v-model="form.brand" name="brand" label=" Brand" icon="barcode" group type="text" validate error="wrong" success="right" trim/>
                        <small class="form-text text-muted red-text" v-show="submitted">
                            {{ errors.first('brand') }}
                        </small>
                        <div>
                            <label>Inventory</label>
                            <mdb-input  v-validate="{required: true}" type="radio" v-model="form.inventoryStatus" name="inventoryStatus" radioValue="true" id="stockTrue" label="In Stock" />
                            <mdb-input type="radio" v-model="form.inventoryStatus" name="inventoryStatus" radioValue="false" id="stockFalse" label="Out of stock" />
                            <small class="form-text text-muted red-text" v-show="submitted">
                            {{ errors.first('inventoryStatus') }}
                        </small>
                        </div>
                        <mdb-textarea v-validate="{required: true}" v-model="form.description" size="sm" :rows="2" name="description" label=" Product description" icon="equals" trim/>
                        <small class="form-text text-muted red-text" v-show="submitted">
                            {{ errors.first('description') }}
                        </small>
                    </mdb-modal-body>
                    <mdb-modal-footer>
                        <mdb-btn type="button" color="secondary" @click.native="showModal = false">Close</mdb-btn>
                        <mdb-btn color="primary" type="submit">Save changes</mdb-btn>
                    </mdb-modal-footer>
                    </mdb-modal>
                </mdb-col>            
            </form>
    </mdb-row>
  </mdb-container>
</template>

<script>
import { mdbContainer, mdbRow, mdbCol, mdbInput, mdbTextarea, mdbBtn, mdbIcon, mdbModal, mdbModalHeader, mdbModalBody, mdbModalFooter } from 'mdbvue';
export default {
    name: 'AddProduct',
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
      mdbModalFooter
    },
    data() {
      return {
        showModal: false,
        form: {
            name: '',
            price: '',
            brand: '',
            inventoryStatus: '',
            description: ''
        },
        submitted: false
      };
    },
    methods: {    
        async onSubmit () {
            this.submitted = true;
            let result = await this.$validator.validate();
            console.log(result);
            if(result) {
                alert('Form has been submitted!');
            } else {
                alert('Correct errors.');
                return;
            }
            
        }
    }
}
</script>

<style>

</style>