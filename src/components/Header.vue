<template>
  <mdb-navbar color="indigo" dark>
        <mdb-navbar-brand href="#">
          Ancap Product Manager
        </mdb-navbar-brand>
    </mdb-navbar>
</template>

<script>
import { mdbNavbar, mdbNavbarBrand } from "mdbvue";
export default {
    name: 'Header',
    components: {
        mdbNavbar, 
        mdbNavbarBrand
    }
}
</script>

<style>

</style>