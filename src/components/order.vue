<template>
    <v-card tile color="#eed459">
        <v-card-title class="text-h5 black--text text-center d-flex justify-center">Your Orders Are Here..</v-card-title>
        <v-card-subtitle-1 class="text-h5 black--text text-center d-flex justify-center"><strong>Happy Shopping..<span class="mdi mdi-cart"></span></strong></v-card-subtitle-1>
        <v-card-subtitle-1 class="text-h6 black--text text-center d-flex justify-center mt-3">Your Order ID : #15641656</v-card-subtitle-1>

        <v-list>
            <v-list-item v-for="item in selectedItems" :key="item.id">
                <v-list-item-avatar>
                        <v-img :src="item.img" height="40" width="40"></v-img>
                 </v-list-item-avatar>
                <v-list-item-content>
                    <v-list-item-subtitle class="black--text">
                        <v-icon color="green" v-if="item.type == 'Veg'">mdi-square-circle</v-icon>
                        <v-icon color="red" v-else-if="item.type == 'Non - Veg'">mdi-square-circle</v-icon>
                        <strong>{{ item.name }}</strong>
                    </v-list-item-subtitle>
                    <v-list-item-subtitle class="black--text"><strong>{{ item.type }}</strong></v-list-item-subtitle>
                </v-list-item-content>
                <v-list-item-action>
                    <v-list-item-subtitle class="black--text mr-3   "><strong>Rs : {{ calculateTotalCost(item) }}</strong></v-list-item-subtitle>
                </v-list-item-action>
                <v-list-item-action>
                    <v-list-item-subtitle class="black--text"><strong>{{ currentDate() }}</strong></v-list-item-subtitle>
                </v-list-item-action>
                <v-list-item-action>
                    <v-list-item-subtitle class="black--text"><strong>{{ currentTime() }}</strong></v-list-item-subtitle>
                </v-list-item-action>
            </v-list-item>
            <div class="text-h6 text-center #eed459"><strong>Bill Amount: {{ billAmount() }}</strong></div>
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
        
    calculateTotalCost(item) {
    const price = parseFloat(item.price.replace("Rs. ", ""));
    const quantity = parseInt(item.quantity);
    return price * quantity;

    },

    currentDate(){
        return new Date().toLocaleDateString();
    },

    currentTime(){
        return new Date().toLocaleTimeString();
    },

    billAmount() {
      return this.selectedItems.reduce((total, item) => {
        return total + this.calculateTotalCost(item);
      }, 0);
    },
    }
}
</script>