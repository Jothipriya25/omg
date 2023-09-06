<template>
  <v-card class="overflow-hidden">
    <v-app-bar
      color="#000000"
      dark
       height="50px"
    >

      <v-app-bar-nav-icon>
        <v-img
            class="logo"
            max-height="80"
            max-width="80"
            style="border-radius: 50%;"
            src="data:image/png;base64,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"
        ></v-img>
      </v-app-bar-nav-icon> 
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        color="#eed459"
        class="mt-10"
      ></v-text-field>

      <v-spacer></v-spacer>

      <v-btn icon color="#eed459">
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon color="#eed459">
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon color="#eed459">
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn> 

      
      <template v-slot:extension>
        
        <v-tabs align-with-title color="#eed459">
            <v-spacer></v-spacer>
          <v-tab @click="menuDialog = true" >Menu</v-tab>
          <v-tab @click="cartDialog = true">Cart</v-tab>
          <v-tab @click="orderDialog = true ">Order</v-tab>
        </v-tabs>
      </template>
    </v-app-bar>

    <v-img

        cover
        height="85vh"
        width="100wh"
        src="https://img.freepik.com/premium-vector/gift-box-gold-bow-ribbon_383392-41.jpg"
        ></v-img>
    
        <v-dialog v-model="menuDialog" fullscreen>
        <v-card color="#FFF9C4" tile>
            <v-card-title>
            <span class="headline"><strong>Products</strong></span>
            <v-spacer></v-spacer>
              <v-icon large @click="cartDialog = true" color="black" >
                mdi-cart
                </v-icon>
            <v-badge
                :content='count'
                overlap
                color="black"
            >
             </v-badge>
             
            </v-card-title>
            <v-card-text>
            <Menu @addbadge="addtobadge($event)" @delbadge="deltobadge($event)" @add-to-cart="addToCart" />
            </v-card-text>
            <v-card-actions class="d-flex justify-center">         
            <v-btn color="black" class="white--text" @click="menuDialog = false">Close</v-btn>
            </v-card-actions>
        </v-card>
    </v-dialog>
    <v-dialog v-model="cartDialog" max-width="900" max-height="800" >
      <Cart  :selectedItems="selectedItems" @add-to-cart="addToOrder" />
      <v-card class="text-right" tile >        
        <v-btn color="#eed459" class="black--text mt-8 mb-6 mr-5" @click="cartDialog = false">Close</v-btn>
        <v-btn color="#eed459" class="black--text mt-8 mb-6 mr-5" @click="orderDialog = true">Order here</v-btn>
      </v-card>
    </v-dialog>
    <v-dialog v-model="orderDialog" max-width="600" max-height="800">
      <Order  :selectedItems="selectedItems"/>
    </v-dialog>
  </v-card>
</template>


<script>

import Menu from './menu.vue';
import Cart from './cart.vue';
import Order from './order.vue';

export default {
    components: {
        Menu,
        Cart,
        Order,
    },

    data(){
        return{
            menuDialog: false,
            cartDialog: false,
            orderDialog: false,
            count:0,
            search:'',
            selectedItems:[],
            uniq:[],
            
        }
    },

    
  
  methods: {
    addtobadge(data){
      this.count=data;
    },
    deltobadge(data){
      this.count=data;
    },
    addToCart(item) {
      if(!this.selectedItems.includes(item))
      // item.quantity++
      this.selectedItems.push(item);
      // this.uniq = this.selectedItems.filter((a, index) => {
      //   return this.selectedItems.indexOf(a)=== (index)});
      //   console.log(this.uniq);
      
    

    },
    addToOrder(item){
      if(!this.selectedItems.includes(item))
        this.selectedItems.push(item);
      
    },
    
  }
}
 
</script>


<style>
    .logo{
        margin-left: 50px;
        margin-top: 50px;
    }
</style>