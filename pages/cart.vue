<template>
    <div>
        <resheader></resheader>
        <b-container class="ct">
            <h1>Cart Page</h1>
            <div class="row">
               <foodselected v-for="product in selectedProducts" :key="product.id" 
                    :name="product.name" 
                    :price="product.price" 
                    :count="product.count"
                    :image="product.image" 
                    class="col-10 offset-1 my-2" >
                </foodselected>
            </div>
        </b-container>
        <resfooter></resfooter>        
    </div>
    
</template>
<script>
import Foodselected from '~/components/Foodselected.vue'
import Resfooter from '~/components/Resfooter.vue'
import Resheader from '~/components/Resheader.vue'

export default {
  components: { Resheader, Foodselected ,Resfooter},
  data(){
      return{
          selectedProducts : []
      }
  },
  mounted(){
      const productJson = this.getCookie('product-selected')
      if(productJson !== ''){
         this.selectedProducts = JSON.parse(productJson)
      }
      
     

  },
  methods: {
      getCookie(cname) {
        const name = cname + "=";
        const decodedCookie = decodeURIComponent(document.cookie);
        const ca = decodedCookie.split(';');
        for(let i = 0; i <ca.length; i++) {
            let c = ca[i];
            while (c.charAt(0) === ' ') {
            c = c.substring(1);
            }
            if (c.indexOf(name) === 0) {
            return c.substring(name.length, c.length);
            }
        }
        return "";
        } 
  }
    
}
</script>
<style scoped>
.ct{
   margin-bottom: 150px; 
}
</style>