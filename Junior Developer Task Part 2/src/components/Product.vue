<template>
  <div id="product">
    <!-- Add your code here -->
    <div class="siderow">
      <div class="imgs">
        <img :src="product.media_gallery[0].image" :width="product.media_gallery[0].width" :height="product.media_gallery[0].height" :alt="product.media_gallery[0].alt"/>
        <img :src="product.media_gallery[1].image" :width="product.media_gallery[1].width" :height="product.media_gallery[1].height" :alt="product.media_gallery[1].alt"/>
        <img :src="product.media_gallery[2].image" :width="product.media_gallery[2].width" :height="product.media_gallery[2].height" :alt="product.media_gallery[2].alt"/>
        <img :src="product.media_gallery[3].image" :width="product.media_gallery[3].width" :height="product.media_gallery[3].height" :alt="product.media_gallery[3].alt"/>
      </div>
      <div class = "text">
        <div class = "offerrow">
          <div class = "redline3"></div>
          <p id = "offer"> {{ product.product_offer_label }}</p>
        </div>

        <p id = "title"> {{ product.product_title }}</p>

        <hr>
        
        <h5>Original Now</h5>
        <h6 id ="price">
          <s>£{{ product.rrp }}.00</s>
          <span class="sell">£{{ product.selling_price }}.00</span>
          <div class="redline"></div> 
          <p>Save {{ percentage }}%</p>
          <div class="redline2"></div> 
        </h6>
        
        <hr>

        <div class = "altimgs">
          <img :src="product.alternative_colours[0].image" :width="product.alternative_colours[0].width" :height="product.alternative_colours[0].height" :alt="product.alternative_colours[0].alt"/>
          <img :src="product.alternative_colours[1].image" :width="product.alternative_colours[1].width" :height="product.alternative_colours[1].height" :alt="product.alternative_colours[1].alt"/>
          <img :src="product.alternative_colours[2].image" :width="product.alternative_colours[2].width" :height="product.alternative_colours[2].height" :alt="product.alternative_colours[2].alt"/>
          <img :src="product.alternative_colours[3].image" :width="product.alternative_colours[3].width" :height="product.alternative_colours[3].height" :alt="product.alternative_colours[3].alt"/>
        </div>

        <hr>

        <div class ="size">
          <p>Select Size</p>
        </div>

        <div class = "sizebtns">
          <button @click="sizebtn(8)">8</button>
          <button @click="sizebtn(10)">10</button>
          <button @click="sizebtn(12)">12</button>
          <button @click="sizebtn(14)">14</button>
          <button @click="sizebtn(16)">16</button>
          <button @click="sizebtn(18)">18</button>
          <button @click="sizebtn(20)">20</button>
        </div>

         <hr>

        <div class = "addtobag">
          <button @click="bagbtn">Add To Bag</button>
        </div>

        <div class = "Description"> 
          <h5>Description</h5>
          <p class="desc">{{ product.product_description }}</p>

          <div class = "poppins-medium" v-html="product.product_bulletpoints"></div>

          <div class = "poppins-regular">
            <p> Product Code: {{ product.product_sku }}</p>
          </div>
        </div>
      </div>
    </div>
    <footer class="footer"></footer>
  </div>
</template>

<script>
import { provide } from 'vue';
import product from '../assets/Product.json'

export default {
  name: 'ProductPage',
  data() {
    return {
      sizeselect: '',
      product: product,
      // Add any other data properties you need
    }
  },
  methods:
  {
    bagbtn()
    {
      if(this.sizeselect == 0)
      {
        alert("You have not selected a size");
      }
      else
      {
        alert("You have selected size: " + this.sizeselect);
      }
    },

    sizebtn(size)
    {
      this.sizeselect=size;
    },

  },
  computed:
  {
    percentage()
    {
      return ((this.product.rrp - this.product.selling_price) / this.product.rrp * 100);
    }
  }
  // Any Vue lifecycle hooks and custom JavaScript code can be added here
}
</script>

<style scoped lang="scss">
// Styling to be added here if needed. SASS is allowed if preferred
.Description h5{
  @extend .poppins-medium;
  font-size: 17px;
  margin-bottom: 20px;
}

.desc {
  @extend .poppins-regular;
  font-size: 14px;
}

#title {
  @extend .poppins-medium;
  margin-bottom: 0px;
  font-size: 18px;
}

#offer {
  @extend .poppins-light;
  font-size: 15px;
  margin: 0px;
}

.poppins-thin {
  font-family: "Poppins", sans-serif;
  font-weight: 100;
  font-style: normal;
}

.poppins-extralight {
  font-family: "Poppins", sans-serif;
  font-weight: 200;
  font-style: normal;
}

.poppins-light {
  font-family: "Poppins", sans-serif;
  font-weight: 300;
  font-style: normal;
}

.poppins-regular {
  font-family: "Poppins", sans-serif;
  font-weight: 400;
  font-style: normal;
}

.poppins-medium {
  font-family: "Poppins", sans-serif;
  font-weight: 500;
  font-style: normal;
}

.poppins-semibold {
  font-family: "Poppins", sans-serif;
  font-weight: 600;
  font-style: normal;
}

.poppins-bold {
  font-family: "Poppins", sans-serif;
  font-weight: 700;
  font-style: normal;
}

.poppins-extrabold {
  font-family: "Poppins", sans-serif;
  font-weight: 800;
  font-style: normal;
}

.poppins-black {
  font-family: "Poppins", sans-serif;
  font-weight: 900;
  font-style: normal;
}

.poppins-thin-italic {
  font-family: "Poppins", sans-serif;
  font-weight: 100;
  font-style: italic;
}

.poppins-extralight-italic {
  font-family: "Poppins", sans-serif;
  font-weight: 200;
  font-style: italic;
}

.poppins-light-italic {
  font-family: "Poppins", sans-serif;
  font-weight: 300;
  font-style: italic;
}

.poppins-regular-italic {
  font-family: "Poppins", sans-serif;
  font-weight: 400;
  font-style: italic;
}

.poppins-medium-italic {
  font-family: "Poppins", sans-serif;
  font-weight: 500;
  font-style: italic;
}

.poppins-semibold-italic {
  font-family: "Poppins", sans-serif;
  font-weight: 600;
  font-style: italic;
}

.poppins-bold-italic {
  font-family: "Poppins", sans-serif;
  font-weight: 700;
  font-style: italic;
}

.poppins-extrabold-italic {
  font-family: "Poppins", sans-serif;
  font-weight: 800;
  font-style: italic;
}

.poppins-black-italic {
  font-family: "Poppins", sans-serif;
  font-weight: 900;
  font-style: italic;
}
</style>
