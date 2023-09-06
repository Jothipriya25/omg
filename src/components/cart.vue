<template>
    <v-card tile color="#eed459">
        <v-card-title class="text-h4 black--text text-center d-flex justify-center">Welcome to Cart<v-icon color="black" right large>mdi-cart</v-icon></v-card-title>
        <v-card-text class=" text-h6 d-flex justify-center">Here You Can See your items added to cart</v-card-text>
        <v-list>
        <v-list-item v-for="item in selectedItems" :key="item.id">
            <v-list-item-avatar>
            <v-img :src="item.img" height="40" width="40"></v-img>
            </v-list-item-avatar>
            <v-list-item-content>
            <v-list-item-title class="text-h6">
              <v-icon color="green" v-if="item.type == 'Veg'">mdi-square-circle</v-icon>
              <v-icon color="red" v-else-if="item.type == 'Non - Veg'">mdi-square-circle</v-icon>
              {{ item.name }} ({{ item.quantity }})</v-list-item-title>
            <v-list-item-subtitle>
              <strong>{{ item.type }}</strong>
            </v-list-item-subtitle>
            <v-list-item-subtitle><strong>{{ item.price}}</strong></v-list-item-subtitle>
            </v-list-item-content>
            <v-list-item-action>
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
                <span class="mx-2">{{ item.quantity }}</span>
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
            </v-list-item-action>
            <v-list-item-action>
            <v-btn icon small @click="removeFromCart(item)">
                <v-icon>mdi-close</v-icon>
            </v-btn>
            </v-list-item-action>
            <v-list-item-action>
            <span><strong>Total Cost: {{ calculateTotalCost(item) }}</strong></span>
            </v-list-item-action>

        </v-list-item>
        <div class="text-h6 text-center #eed459"><strong>Bill Amount: {{ billAmount() }}</strong></div>
        <!-- <div class="text-center">
          <v-btn class="mt-2 mb-2" color="pink lighten-4" @click="addToOrder(item)" >Order
            <v-icon>mdi-cart</v-icon>
          </v-btn>
        </div> -->
        </v-list>
    </v-card>
</template>

<script>
export default {

    props: {
    selectedItems: {
      type: Array,
      default: () => []
    }
    },

    data() {
        return{
        }
    },
    methods: {


    increase(item) {
        item.quantity++;
    },

    decrease(item) {
        if (item.quantity > 0) {
            item.quantity--;
        }

    },
    removeFromCart(items){
      this.selectedItems.splice(this.selectedItems.indexOf(items),1);
      
    },

    calculateTotalCost(item) {
    const price = parseFloat(item.price.replace("Rs. ", ""));
    const quantity = parseInt(item.quantity);
    return price * quantity;

    },

    billAmount() {
      return this.selectedItems.reduce((total, item) => {
        return total + this.calculateTotalCost(item);
      }, 0);
    },

    addToOrder(item){
      if(this.selectedItems!=0 )
          {
          this.$emit("add-to-order", item);
          }
    }
    }
};

</script>

