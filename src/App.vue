<template>
  <div id="app">

      <ul class="first">
        <h1>Cart list</h1>
        <li v-for="item in products" :key="item.id" class="box">
          <img class="img" :src="item.sources" />
          <b>{{ item.name }}</b>
          <ul>
            <li class="a">
              <span id="q">{{ item.quantity }}</span>
            </li>
            <li class="d">Rs {{ item.cost }}</li>
          </ul>
        </li>
      </ul>

      <ul class="first" v-if="seen">
        <li>
          <img class="img" :src="sr" />
          <button class="clk" @click="add">+</button>
          <span id="r">{{ counter }}</span>
          <button class="clk" @click="sub">-</button>
          <button class="rm" @click="remove">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-x-lg"
              viewBox="0 0 16 16"
            >
              <path
                d="M1.293 1.293a1 1 0 0 1 1.414 0L8 6.586l5.293-5.293a1 1 0 1 1 1.414 1.414L9.414 8l5.293 5.293a1 1 0 0 1-1.414 1.414L8 9.414l-5.293 5.293a1 1 0 0 1-1.414-1.414L6.586 8 1.293 2.707a1 1 0 0 1 0-1.414z"
              />
            </svg>
          </button>
        </li>
      </ul>
      <div class="first">
        <h2>Total cost is</h2>
        <span>Rs: {{ sum }}</span>
      </div>
    </div>
  
</template>

<script>


export default {
  name: 'App',
  components: {

  },
  data() {
    return {
      counter: 1,
      sum: 700,
      price: 500,
      sr: "https://rukminim1.flixcart.com/image/416/416/kg8avm80/mobile/y/7/n/apple-iphone-12-dummyapplefsn-original-imafwg8dpyjvgg3j.jpeg?q=70",
      seen: true,
      products: [
        {
          id: 1,
          sources: "https://rukminim1.flixcart.com/image/880/1056/juk4gi80/sunglass/z/f/f/58-0rb36899064s258-ray-ban-original-imaffhq2kq5rg6xz.jpeg?q=50",
          name: "RayBan Sun glass for men",
          quantity: 1,
          cost: 200
        },
        {
          id: 2,
          sources: "https://rukminim1.flixcart.com/image/416/416/kg8avm80/mobile/y/7/n/apple-iphone-12-dummyapplefsn-original-imafwg8dpyjvgg3j.jpeg?q=70",
          name: "Apple Iphone Blue (128gb)",
          quantity: 1,
          cost: 500
        }
      ]
    }
  },
  methods: {
    add() {
      this.counter += 1,
        this.sum = (this.counter * this.price) + 200
    },
    sub() {
      if (this.counter <= 0) {
        this.counter = 0,
          this.sum = 200
      }
      else {
        this.counter -= 1,
          this.sum = this.sum - this.price
      }
    },
    remove() {
      this.seen = false
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #1d2b2f;
  margin-top: 60px;
  width:95%;
    
 justify-content:center;
}
h1{
  text-align:center;
}
.box {
  width: 100%;
  display: flex;
  background: #b0c9cf;
  margin: 20px auto;
  border: none;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
img {
  width: 70px;
  height: 70px;
  padding-right: 20px;
}
.first {
  border: 1px solid black;
  list-style-type: none;
  width: 60%;
  padding: 10px;
  justify-content: center;
  margin-bottom: 0;
  background: #eff4f5;
}
#q {
  background-color: #45676e;
  color: white;
  padding: 10px;
  border-radius: 100px;
}
.a {
  list-style-type: none;
  padding: 10px;
}
#r {
  padding-left: 12px;
  padding-right: 12px;
  justify-content: center;
  background-color: white;
}
.c {
  padding: 30px;
  padding-left: 90px;
  padding-right: 90px;
  background-color: gray;
  float: left;
}
.d {
  list-style-type: none;
}
b {
  padding-right: 70px;
}
.clk {
  cursor: pointer;
  border: none;
  color: white;
  padding: 5px 15px;
  background-color: rgb(29, 26, 26);
}
.rm {
  cursor: pointer;
  border: none;
  background-color: rgb(221, 94, 94);
  padding: 10px 70px;
  margin-left: 80px;
}
@media screen and (max-width: 899px) {
  .first {
    width: 100%;
  }
}
@media screen and (min-width: 900px) {
  .first {
    width: 40%;
  }
}
</style>