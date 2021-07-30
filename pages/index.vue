<template>
    <div>
        <resheader></resheader>
        <b-container class="mb-5">
            <h1 class="mt-3">Shop Page</h1>
            <div class="row">
                <div v-for="product in products"  :key="product.id" class="col-12 col-lg-6 col-xl-4 my-2">
                  <food :id="product.id" :name="product.name" :price="product.price" :image="product.image"></food>
                </div>
            </div>
        </b-container>
    </div>
</template>
<script>
import Food from '~/components/Food.vue'
import Resheader from '~/components/Resheader.vue'

export default {
  components: { Resheader, Food },
  
  data(){
      return{
          products: [
              {
                  id: 1,
                  name: 'pizza',
                  price: 300,
                  image: 'https://images.unsplash.com/photo-1513104890138-7c749659a591?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80'
              },
              {
                  id: 2,
                  name: 'pancake',
                  price: 100,
                  image: 'https://images.unsplash.com/photo-1471478108131-9b2335c21611?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80'
              },
              {
                  id: 3,
                  name: 'friench fries',
                  price: 50,
                  image: 'https://images.unsplash.com/photo-1552895638-f7fe08d2f7d5?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=967&q=80'
              },
              {
                  id: 4,
                  name: 'steak',
                  price: 500,
                  image: 'https://images.unsplash.com/photo-1542365887-1149961dccc7?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80'
              },
              {
                  id: 5,
                  name: 'ice cream cone',
                  price: 100,
                  image: 'https://images.unsplash.com/photo-1506444187582-b55b5c08d677?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80'
              },
              {
                  id: 6,
                  name: 'hamburger',
                  price: 150,
                  image: 'https://images.unsplash.com/photo-1556710807-aa697ab9e415?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80'
              },
              {
                  id: 7,
                  name: 'banana',
                  price: 10,
                  image: 'https://images.unsplash.com/photo-1481349518771-20055b2a7b24?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1409&q=80'
              },

          ]
      }
  }
    
}
</script>
<style scoped>

</style>
