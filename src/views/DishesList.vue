<template>
  <div id="dishesList">
    <div class="ui fixed inverted menu vue-color">
      <div class="ui container">
        <a href="#" class="header item">CRUD Vue and API</a>
      </div>
    </div>
    <div class="ui main container"></div>
    <DishForm/>
    <Loader v-if="loader" />
    <Dishes :dishes="dishes" @onDelete="onDelete" />
    
  </div>
</template>

<script>
import axios from 'axios';
import DishForm from '@/components/DishForm.vue'
import Dishes from '@/components/Dishes.vue'
import Loader from '@/components/Loader.vue'

export default {
  name: 'DishesList',
  components: {
    DishForm,
    Dishes,
    Loader
  },

  data () {
    return {
      url: "http://localhost/apiPotsman/public/api/dishes",
      dishes: [],
      loader: false
    };
  },

  methods: {
    getDishes() {
      this.loader = true;

      axios.get(this.url).then(data => {
        this.dishes = data.data;
        this.loader = false;
      });
    },
    deleteDish(id) {
      this.loader = true;
      
      axios.delete(`${this.url}/${id}`).then(() => {
        this.getDishes();
      })
      .catch(e =>{
        alert(e);
      });
    },
    onDelete(id) {
      // console.log("DishesList delete" + id);
      this.deleteDish(id);
    }
  },

  created() {
    this.getDishes();
  }
};

</script>

<style>
.vue-color {
  background: #41b883;
}

.main.container {
  margin-top: 60px;
}

.submit-button {
  margin-top: 24px !important;
  float: right;
}

.data{
  margin-top: 15px;
}

thead tr th{
  background: #e0e0e0 !important
}

.ui.inverted.dimmer{
  background: rgba(255, 255, 255, 0) !important;
}
</style>
