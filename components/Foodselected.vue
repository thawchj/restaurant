<template>
    <div class="my-item row">
        <div class="col-12 col-md-4 col-lg-3 p-0">
            <img height="auto" width="100%" :src="image" alt="">
        </div>
        <div class="col-12 col-md-4 col-lg-5">
            <h2><b>{{name}}</b></h2>
            <h5>ราคา {{price}} บาท</h5>
        </div>
        <div class="col-12 col-md-4 col-lg-4 text-center">
            <div>
                <span class="item-count">{{count}}</span><span style="font-size: 24px">ชิ้น</span>
            </div>
            <div class="total-price">
                {{ count * price}} บาท
            </div>
        </div>
    </div>
</template>
<script>
export default {
   props:{
       name: {
           type: String,
           default: ''
       },
       price: {
           type: Number,
           default: 0
       },
       count: {
           type: Number,
           default: 0 
       },
       image: {
           type: String,
           default: ''
       }
   }
}
</script>

<style  scoped>
    .my-item{
        width: 100%;
        padding: 10px;
        background-color: rgb(221, 221, 221); 
        border-radius: 2px; 
    }
    .item-count{
        font-size: 50px;
        font-weight: bold;
        margin-right: 10px;
    }
    .total-price{
        font-size: 14px;
        color: rgb(57, 57, 58);
    }
    
</style>