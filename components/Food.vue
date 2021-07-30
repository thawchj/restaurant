<template>
    <div class="my-item">
        <img :src="image" width="100%" height="auto">
        <div class="d-flex justify-content-between mt-2">
            <div class="food-name">{{name}}</div>
            <div class="food-price">{{price}} บาท</div>
        </div>
        <b-form-input v-model="count" type="number" class="my-2" placeholder="ใส่จำนวน"></b-form-input>
        <b-button  @click="addToCart()" variant="dark" class="w-100">ADD</b-button>
    </div>
</template>
<script>
export default {
    props: {
        id: {
            type: Number,
            default: 0
        },
        name:{
            type: String,
            default: ''
        },
        price: {
            type: Number,
            default: 0
        },
        image:{
            type: String,
            default: ''
        }

    },
    data(){
        return{
            count: 0
        }
    },
    methods: {
        addToCart(){
            const item = {
                id: this.id,
                name: this.name,
                price: this.price,
                count: parseInt(this.count),
                image: this.image
            }

            // 1.ดึงค่าจาก คุ๊กกี้ แล้วเช็คว่า มีตัวแปร product-selected หรือยัง
            const productSelected = this.getCookie('product-selected')
            if(productSelected === ''){
                // 1.1 ถ้ายังไม่มี product-selected ให้เพิ่มเข้าไป
                const itemJSON = JSON.stringify([item])
                this.setCookie('product-selected',itemJSON,5)
            }else{
                // 1.2 ถ้ามี product-selected แล้วให้เช็คค่า ด้านในว่า มีสินค้าที่เราเลือกอยู่ใน product-selectedแล้วหรือยัง
                const productSelectedArr = JSON.parse(productSelected)
                const isSelected = productSelectedArr.some(p => p.id === item.id)
                // 1.2.1 ถ้ายังไม่มีสินค้า ที่เลือก ใน product-selected ให้ push สินค้าเข้าไปได้เลย
                if (isSelected === false){
                    productSelectedArr.push(item)
                    const productSelectedArrJson = JSON.stringify(productSelectedArr)
                    this.setCookie('product-selected',productSelectedArrJson,5)
                }
                // 1.2.2 ถ้ามีสินค้าที่เลือก ใน product-selected ให้ count ของสินค้านั้น เพิ่มตามที่ user กรอกเข้ามา
                else{
                    for(let i = 0 ;i < productSelectedArr.length; i++){
                        if(productSelectedArr[i].id === item.id){
                            productSelectedArr[i].count += item.count
                        }
                    }
                    const productSelectedArrJson = JSON.stringify(productSelectedArr)
                    this.setCookie('product-selected',productSelectedArrJson,5)
                }
            }
            
             
            
            



           
           
        },
        setCookie(cname, cvalue, exdays) {
        const d = new Date();
        d.setTime(d.getTime() + (exdays*24*60*60*1000));
        const expires = "expires="+ d.toUTCString();
        document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
        },
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

<style  scoped>
    .my-item{
        padding: 10px;
        background-color: rgb(252, 237, 245);
        border-radius: 3px;
        -webkit-box-shadow: 11px 10px 19px -17px rgba(0,0,0,0.75);
        -moz-box-shadow: 11px 10px 19px -17px rgba(0,0,0,0.75);
        box-shadow: 11px 10px 19px -17px rgba(0,0,0,0.75);
    }
    .my-item:hover{
        -webkit-box-shadow: 11px 10px 19px -14px rgba(0,0,0,0.75);
        -moz-box-shadow: 11px 10px 19px -14px rgba(0,0,0,0.75);
        box-shadow: 11px 10px 19px -14px rgba(0,0,0,0.75);
    }
    .food-name{
        font-weight: bolder;
        font-size: 20px;
        color: rgb(48, 47, 47);
    }
    .food-price{
        font-size: 20px;
        color: rgb(58, 58, 56);
    }
</style>