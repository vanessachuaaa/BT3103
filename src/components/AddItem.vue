<template>
  <div id=app>
    <h1>Add Item Page</h1>
    <form id="fm1">
        <label>Item Name:</label>
        <input type="text" v-model.lazy="item.name" required/>
        <br>

        <label> Item Category: </label>
        <input type="checkbox" id ="checkbox1" v-model.lazy="item.category" value = "Snack"/><label for="checkbox1">Snack</label>
        <input type="checkbox" id ="checkbox2" v-model.lazy="item.category" value = "Meal"/> <label for="checkbox2">Meal</label>
        <input type="checkbox" id ="checkbox3" v-model.lazy="item.category" value = "Tea Break"/><label for="checkbox3">Tea Break</label>
        <br>
     
        <label> Item Type: </label>
        <input type="radio" id="optionA" name="radioBtn" value="Food" v-model.lazy="item.type" /><label for="optionA">Food</label>
        <input type="radio" id="optionB" name="radioBtn" value="Drink" v-model.lazy="item.type" /><label for="optionB">Drink</label>
        
        <br>
        <button v-on:click.prevent="addItem">Add Item</button>
    </form>
  </div>
</template>

<script>

import database from '../firebase.js'
export default {

  data(){
    return{
        msg:"Add Item",
        item:{
          name:'',
          category: [],
          type: '',
        },
        
        
      }
  },
  methods:{
    addItem:  function () {
          //Save item to database
          database.collection('items').doc().set(this.item);
          this.item.name="";
          this.item.category= [];
          this.item.type = "";
          alert("I am in the DB .... :-) Item saved successfully")
          
        }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#app *{
    box-sizing: border-box;
}
#app{
    margin: 20px auto;
    max-width: 700px;
}

p{
    align-content: center;
    color:ivory;
}
label{
    display: inline-block;
    margin: 20px 0 10px;
    width:15%;
    align-content:left;

}
input[type="text"]{
    display: inline-block;
    padding: 8px;
    width:50%;
}
input[type = "checkbox"] {
  width:5%;
}
</style>