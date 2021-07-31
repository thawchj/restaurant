<template>
  <div>
    <div class="cardimg">
      <div
        class="imgbg"
        :style="{
          backgroundImage: `linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)), url(${image})`,
        }"
      ></div>
      <div class="moutain-in">
        <div class="container-fluid">
          <div class="row">
            <div class="col-10 col-lg-8 p-md-5 p-4">
              <div class="texthead-in">{{ name }}</div>
              <p class="text-in">
                Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                Soluta, consectetur dolore rem voluptatibus saepe officiis at
                cum tenetur itaque alias veritatis
              </p>
              <button class="button-order">order now</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    id: {
      type: Number,
      default: 0,
    },
    name: {
      type: String,
      default: '',
    },
    price: {
      type: Number,
      default: 0,
    },
    image: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      count: 0,
    }
  },
  methods: {
    addToCart() {
      const item = {
        id: this.id,
        name: this.name,
        price: this.price,
        count: parseInt(this.count),
        image: this.image,
      }

      // 1.ดึงค่าจาก คุ๊กกี้ แล้วเช็คว่า มีตัวแปร product-selected หรือยัง
      const productSelected = this.getCookie('product-selected')
      if (productSelected === '') {
        // 1.1 ถ้ายังไม่มี product-selected ให้เพิ่มเข้าไป
        const itemJSON = JSON.stringify([item])
        this.setCookie('product-selected', itemJSON, 5)
      } else {
        // 1.2 ถ้ามี product-selected แล้วให้เช็คค่า ด้านในว่า มีสินค้าที่เราเลือกอยู่ใน product-selectedแล้วหรือยัง
        const productSelectedArr = JSON.parse(productSelected)
        const isSelected = productSelectedArr.some((p) => p.id === item.id)
        // 1.2.1 ถ้ายังไม่มีสินค้า ที่เลือก ใน product-selected ให้ push สินค้าเข้าไปได้เลย
        if (isSelected === false) {
          productSelectedArr.push(item)
          const productSelectedArrJson = JSON.stringify(productSelectedArr)
          this.setCookie('product-selected', productSelectedArrJson, 5)
        }
        // 1.2.2 ถ้ามีสินค้าที่เลือก ใน product-selected ให้ count ของสินค้านั้น เพิ่มตามที่ user กรอกเข้ามา
        else {
          for (let i = 0; i < productSelectedArr.length; i++) {
            if (productSelectedArr[i].id === item.id) {
              productSelectedArr[i].count += item.count
            }
          }
          const productSelectedArrJson = JSON.stringify(productSelectedArr)
          this.setCookie('product-selected', productSelectedArrJson, 5)
        }
      }
    },
    setCookie(cname, cvalue, exdays) {
      const d = new Date()
      d.setTime(d.getTime() + exdays * 24 * 60 * 60 * 1000)
      const expires = 'expires=' + d.toUTCString()
      document.cookie = cname + '=' + cvalue + ';' + expires + ';path=/'
    },
    getCookie(cname) {
      const name = cname + '='
      const decodedCookie = decodeURIComponent(document.cookie)
      const ca = decodedCookie.split(';')
      for (let i = 0; i < ca.length; i++) {
        let c = ca[i]
        while (c.charAt(0) === ' ') {
          c = c.substring(1)
        }
        if (c.indexOf(name) === 0) {
          return c.substring(name.length, c.length)
        }
      }
      return ''
    },
  },
}
</script>

<style  scoped>
.texthead-in {
  font-size: 7vh;
  font-weight: bold;
}
.text-in {
  font-size: 2vh;
}
.cardimg {
  background-color: white;
}
.imgbg {
  min-height: 50vh;
  background-position: center;
  background-size: cover;
  position: relative;
  width: 100%;
}

.food-name {
  font-weight: bolder;
  font-size: 20px;
  color: rgb(48, 47, 47);
}
.food-price {
  font-size: 20px;
  color: rgb(58, 58, 56);
}
.moutain-in {
  position: absolute;
  z-index: 2;
  top: 0%;
  left: 0%;
  color: white;
}
.button-order {
  font-size: 2vh;
  background: none;
  cursor: pointer;
  border: 0.15vw solid white;
  color: white;
  border-radius: 0.2vh;
  padding: 0.5vh 1.2vh 0.5vh 1.2vh;
}
</style>