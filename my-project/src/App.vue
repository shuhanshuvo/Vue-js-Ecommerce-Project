<template>
  <div id="app">
   
  <navbar @search="search"></navbar>
          <div class="container">
            <div class="row">
              <div class="col-sm-10">
          <inventory @newItemAdded="addCartItem" :items="items"> </inventory> 
          </div>       
             <div class="col-sm-2">
               <cart @itemRemove="removeItem" :items="cart"></cart>

             </div>
             </div>
             </div>
          </div>

          

</template>

<script>
import Navbar from './components/Navbar'
import cart from './components/cart'
import inventory from './components/inventory'
import data from './data.js'
export default {
  components:{
    Navbar,
    cart,
    inventory
  },
  data(){
    return{
      items: [],
      cart: []

    }
  },
  mounted(){
    this.items = data
  },
  methods:{
    search(keyword){
     this.items = data.filter(item=>{
       return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !== -1
     })
    },
    addCartItem(item){
      this.cart.push(item)
    },
    removeItem(index){
      this.cart.splice(index, 1)
    }
  }

}
</script>


<style>
.container{
  padding-top:10px;
}

</style>
