<template>
    <div>
        <div class="img-top">
            <resheader></resheader>
            <h1 class="top-text">ARE YOU HUNGRY ? don't wait let start to order food now</h1>
        </div>
        <div class="mb-5">
            <h1 class="mt-3">Choose & enjoy</h1>
            <div class="container-fluid">
                <div class="row">
                        <div  v-for="product in products"  :key="product.id" class="col-12 col-lg-6 px-0 py-lg-2">
                            <div v-if="product.id%2 !== 0">
                                <food  class="pr-0 pr-lg-2" :id="product.id" :name="product.name" :price="product.price" :image="product.image"></food>
                            </div>
                            <div v-if="product.id%2 === 0">
                                <food  class="pl-0 pl-lg-2 " :id="product.id" :name="product.name" :price="product.price" :image="product.image"></food>
                            </div>
                        </div> 
                         
                </div>
            </div>
            
        </div>
    </div>
</template>
<script>
import Food from '~/components/Food.vue'
import Resheader from '~/components/Resheader.vue'

export default {
  components: { Resheader, Food  },
  
  data(){
      return{
          products: [
              {
                  id: 1,
                  name: 'Carbonara Pasta',
                  price: 10,
                  image: 'https://images.unsplash.com/photo-1612874742237-6526221588e3?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1951&q=80' 
              },
              {
                  id: 2,
                  name: 'salad',
                  price: 100,
                  image: 'https://images.unsplash.com/photo-1529059997568-3d847b1154f0?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80'
              },
              {
                  id: 3,
                  name: 'friench fries',
                  price: 50,
                  image: 'https://images.unsplash.com/photo-1529692236671-f1f6cf9683ba?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1050&q=80'
              },
              {
                  id: 4,
                  name: 'steak',
                  price: 500,
                  image: 'https://images.unsplash.com/photo-1585703900468-13c7a978ad86?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1950&q=80'
              },
              {
                  id: 5,
                  name: 'ice cream cone',
                  price: 100,
                  image: 'https://images.unsplash.com/photo-1580559489333-755f7e3c8949?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1950&q=80'
              },
              {
                  id: 6,
                  name: 'hamburger',
                  price: 150,
                  image: 'https://images.unsplash.com/photo-1556710807-aa697ab9e415?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80'
              }
              

          ]
      }
  }
    
}
</script>
<style scoped>

.img-top {
  background-image: linear-gradient(rgba(0, 0, 0, 0.0), rgba(0, 0, 0, 0.500)),
    url(https://images.unsplash.com/photo-1553527922-767df645c5f6?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1950&q=80);
  min-height: 75vh;
  background-position: center;
  background-size: cover;
  position: relative;
  width: 100%;
}
.top-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 100%;
  padding: 20px 15px;
  text-align: center;
  color: rgb(255, 255, 255);
  font-size: 10vh;
}

</style>
