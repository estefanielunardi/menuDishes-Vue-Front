<template>
    <div class="dishes">
       <div class="data">
           <table class="ui celled table">
               <thead>
                   <tr>
                       <th style="width: 50px; text-align: center;">#</th>
                       <th>Image</th>
                       <th>Plate Name</th>
                       <th>Price</th>
                       <th>Description</th>
                       <th style="width: 148px;">Action</th>
                   </tr>
               </thead>

               <tbody>
                   <Dish 
                   v-for="dish in dishes" 
                   :key="dish.id" 
                   :dish="dish" 
                   @onDelete="onDelete"
                   />
               </tbody>
           </table>
       </div>
    </div>
</template>

<script>
import Dish from './Dish.vue'
export default {
    name: 'Dishes',
    components: {
        Dish
    },
    props: {
        dishes: {
            type: Array
        }
    },
    methods: {
        onDelete(id) {
            // console.log("dishes delete" + id);
            this.$emit("onDelete" , id);
        }
    }
};

</script>

<style scoped>
</style>