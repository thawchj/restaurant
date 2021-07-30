<template>
    <div class="my-header">
        <b-container :class="currentPage === 'cart' ? 'd-flex justify-content-between' : 'text-right'">
            <nuxt-link v-if="currentPage === 'cart'" to="/">
                <b-icon icon="arrow-left-square-fill" animation="cylon" variant="dark" font-scale="2"  class="mt-3"></b-icon>
            </nuxt-link>
            <nuxt-link to="/cart">
                <b-icon icon="cart2" variant="warning" animation="cylon" font-scale="2" class="mt-3"></b-icon><b-badge variant="light" size="sm">9</b-badge>    
            </nuxt-link>
        </b-container>
    </div>
</template>
<script>
export default {
    data(){
        return{
            currentPage: this.$route.name
        }
    }
    
}
</script>
<style scoped>
    .my-header{
        width: 100%;
        height: 70px;
        background-color: rgb(247, 9, 128);
        -webkit-box-shadow: 11px 10px 19px -10px rgba(0,0,0,0.75);
        -moz-box-shadow: 11px 10px 19px -10px rgba(0,0,0,0.75);
        box-shadow: 11px 10px 19px -10px rgba(0,0,0,0.75);
    }
</style>