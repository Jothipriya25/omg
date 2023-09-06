<template>
    <v-container class="pa-4 text-center" style="max-width: 1200px;">
        <v-row
          class="fill-height"
          align="center"
          justify="center"
          
        >
          <template v-for="(item, i) in items">
            <v-col
              :key="i"
              cols="12"
              md="3"
              mb="2"
              
            >
          <v-card width="300px" elevation="8" color="white" rounded >
          <v-img
            height="220"
            :src="item.img"
            cover
          ></v-img>
      
          <v-card-title class="text-h6 black--text "><strong>{{ item.name }}</strong></v-card-title>
      
          <v-card-text>
            <v-row 
              class="mx-0 mt-0"
            >
              <div class="text-h6 black--text">
                <strong>{{item.type}}</strong>
              </div>
    
            </v-row>

            <v-row 
              align="center"
              class="mx-0 mt-4 mb-6"
    
            >
              <div class="text-h6 black--text">
                <strong>{{item.price}}</strong>
              </div>
    
            </v-row>
    
            <v-row >
                <div class="text-h6">
                    <v-btn
                    fab
                    rounded
                    x-small
                    color="error"
                    @click="decrease(item)"
                    
                    >
                        <v-icon dark >mdi-minus</v-icon>
                    </v-btn>
                    <span class="black--text mx-2">{{ item.quantity }}</span>
                    <v-btn
                    fab
                    rounded
                    x-small
                    color="success"
                    @click="increase(item)"
                    >
                        <v-icon dark>mdi-plus</v-icon>
                    </v-btn>
    
                </div>
                <v-spacer></v-spacer>
                <v-btn
                    rounded
                    depressed
                    color="pink lighten-3"
                    :disabled="item.quantity===0"
                    class="black--text mb-5"
                    @click="addToCart(item)"
                    >
                    <strong>{{ item.add }}</strong>
                </v-btn>
            </v-row>
    
        </v-card-text>
          </v-card>
            </v-col>
          </template>
        </v-row>
        </v-container>
      </template>
    
    <script>
    export default {
    
        
    
      data: () => ({
        badgeCount: 0,
        items: [
          {
            name: "Mug",
            price:"Rs. 200",
            type: `Gift this to ur loved ones..`,
            img:'https://assets.winni.in/product/primary/2022/8/72629.jpeg?dpr=2&w=220' ,
            add: 'Add to Cart',
            quantity:0,
            },
          {
            name: "Caricature",
            price:"Rs. 300",   
            type: `Gift this to ur loved ones..`,
            img: 'https://homafy.com/wp-content/uploads/2023/01/valentine-caricature.jpeg' ,
            add: 'Add to Cart',
            quantity:0,
            },
          {
            name: "Cushion",
            type: `Gift this to ur loved ones..`,
            price:"Rs. 200",
            img:'https://homafy.com/wp-content/uploads/2023/06/Anniversary-pillow.jpg',
            add: 'Add to Cart',
            quantity:0,
          },
          {
            name: "Teddy Bear",
            type: `Gift this to ur loved ones..`,
            price:"Rs. 250",     
            img: 'https://rukminim2.flixcart.com/image/850/1000/jtaed8w0/stuffed-toy/g/x/g/4-feet-soft-plush-teddy-bear-perfact-gift-for-girl-boy-kids-and-original-imafdk5pwztsvhnh.jpeg?q=20' ,
            add: 'Add to Cart',
            quantity:0,
          },
          {
            name: "Photo Frame",
            type:`Gift this to ur loved ones..`,
            price:"Rs. 300",     
            img: 'https://cms.cloudinary.vpsvc.com/image/upload/c_scale,dpr_auto,f_auto,q_auto:best,t_productPageHeroGalleryTransformation_v2,w_auto/india%20lob/photo%20frames/in_photo-with-frame_001' ,
            add: 'Add to Cart',
            quantity:0,
          },
          {
            name: "Name Board",
            type: `Gift this to ur loved ones..`,
            price:"Rs. 500",     
            img: 'https://www.woodgeekstore.com/cdn/shop/products/wooden-nameplate-for-lawyers-set-of-3-square_0afa7d78-565f-440c-ad9d-4a7f3654d5f4_1024x1024.jpg?v=1650624840' ,
            add: 'Add to Cart',
            quantity:0,
          },
          {
            name: "Mug",
            price:"Rs. 200",
            type: `Gift this to ur loved ones..`,
            img:'https://assets.winni.in/product/primary/2022/8/72629.jpeg?dpr=2&w=220' ,
            add: 'Add to Cart',
            quantity:0,
            },
          {
            name: "Caricature",
            price:"Rs. 300",   
            type: `Gift this to ur loved ones..`,
            img: 'https://homafy.com/wp-content/uploads/2023/01/valentine-caricature.jpeg' ,
            add: 'Add to Cart',
            quantity:0,
            },
    
        ], 
      }),
    
        methods: {
    
            increase(item) {
            item.quantity++;
              this.badgeCount++;
              this.$emit("addbadge",this.badgeCount)
            },
            decrease(item) {
            if (item.quantity > 0) {
                item.quantity--;
                this.badgeCount--;
                this.$emit("delbadge",this.badgeCount)
            }
            },
    
            addToCart(item) {
              if(item.quantity!=0 )
              {
              console.log(item , 'item');
              this.$emit("add-to-cart", item);
              }
            }
            }
    };
    </script>
    <style>
    
    </style>