<template>
 <mdb-container>
    <mdb-row>
        <ValidationObserver v-slot="{ invalid }">
            <form @submit.prevent="onSubmit">
                <mdb-col size="12" class="text-center mb-5">
                    <mdb-btn @click.native="showModal = true" type="button" color="info">Add New Product</mdb-btn>
                    <mdb-modal :show="showModal" @close="showModal = false" cascade class="text-left">
                    <mdb-modal-header class="primary-color white-text">
                        <h4 class="title"><span class="fa fas fa-pencil-alt" /> Add New Product</h4>
                    </mdb-modal-header>
                    <mdb-modal-body class="grey-text">
                        <ValidationProvider name="form.name" rules="required" v-slot="{ errors }">
                            <mdb-input size="sm" v-model="form.name" name="name" label=" Product name" icon="file-signature" group type="text" validate error="wrong" success="right" trim/>
                            <span>{{ errors[0] }}</span>
                        </ValidationProvider>

                        <mdb-input size="sm" v-model="form.price" name="price" label="  Product price" icon="money-bill" group type="text" validate error="wrong" success="right" trim/>
                        <mdb-input size="sm" v-model="form.brand" name="brand" label=" Brand" icon="barcode" group type="text" validate error="wrong" success="right" trim/>
                        <div>
                            <label>Inventory</label>
                            <mdb-input type="radio" v-model="form.inventoryStatus" name="inventoryStatus" radioValue="true" id="stockTrue" label="In Stock" />
                            <mdb-input type="radio" v-model="form.inventoryStatus" name="inventoryStatus" radioValue="false" id="stockFalse" label="Out of stock" />
                        </div>
                        <mdb-textarea v-model="form.description" size="sm" :rows="2" name="description" label=" Product description" icon="equals" trim/>
                    </mdb-modal-body>
                    <mdb-modal-footer>
                        <mdb-btn type="button" color="secondary" @click.native="showModal = false">Close</mdb-btn>
                        <mdb-btn color="primary" :disabled="invalid" type="submit" @click="addProduct()">Save changes</mdb-btn>
                    </mdb-modal-footer>
                    </mdb-modal>
                </mdb-col>            
            </form>
        </ValidationObserver>
    </mdb-row>
  </mdb-container>
</template>

<script>
import { mdbContainer, mdbRow, mdbCol, mdbInput, mdbTextarea, mdbBtn, mdbIcon, mdbModal, mdbModalHeader, mdbModalBody, mdbModalFooter } from 'mdbvue';
import { ValidationProvider, ValidationObserver, extend } from 'vee-validate';
import { required, email } from 'vee-validate/dist/rules';
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
      mdbModalFooter,
      ValidationProvider,
      ValidationObserver
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
        }
      };
    },
    methods: {
        addProduct() {
            console.log(this.form);
        },
        onSubmit () {
            alert('Form has been submitted!');
        }
    }
}
</script>

<style>

</style>