<template>
    <div>
        <ul>
            <li v-for="(menu_item,index) in menu_data" :key="menu_item.name">
                <button @click="increment(index)">  {{menu_item.name}}</button>
                <br><br>
            </li>
        </ul>
        <hr><hr>
        <ul>
            <li v-for="item in cart">
                <div v-if="item.quantity > 0">{{item.name}} X {{item.quantity}} = ${{item.extended_price}}
                    </div>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "MenuGrid",
        data(){
          return{
              menu_data:[
                  {'name':'Grilled Chicken Sandwich', 'price':10.00, 'quantity':0},
                  {'name':'Spicy Chicken Sandwich', 'price':10.00, 'quantity':0},
                  {'name':'Lloyds Meatloaf', 'price':10.00, 'quantity':0},
                  {'name':'Dustins  Vege Burger', 'price':10.00, 'quantity':0},
              ]
          }
        },
        computed:{
            cart(){
                var temp_cart = []
                for (var menu_item in this.menu_data){

                        let item_with_price ={
                            'name': this.menu_data[menu_item]['name'],
                            'quantity': this.menu_data[menu_item]['quantity'],
                            'extended_price': this.menu_data[menu_item]['price'] * this.menu_data[menu_item]['quantity']
                            }

                        if (item_with_price['quantity'] > 0){
                            temp_cart.push(item_with_price)
                        }

                        }
                return temp_cart

            }

        },

        methods:{
            increment(index){
                this.menu_data[index]['quantity'] ++
                console.log(this.menu_data[index])
            }
        }
    }
</script>

<style scoped>

</style>