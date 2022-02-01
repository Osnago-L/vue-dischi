<template>
  <div class="main">
    <Select
    @search="getSearchedArray"
    :info="artists"
    ></Select>
    <div class="cards">
    <Cards
      v-for="element,index in test"
      :key="index"
      :info="element"
    />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Cards from './Cards.vue'
import Select from './Select.vue';

export default {
    name: "Main",
    components: {
    Cards,
    Select
    },
  data () {
    return {
      artists: [],
      searched:[]
    }
  },
  created: function(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
          .then((result)=> {
            // handle success
            console.log(result.data.response);
            this.artists = result.data.response;
            this.searched = this.artists
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          })
          .then(function () {
            // always executed
          });
  },
  methods:{
    getSearchedArray: function(selected){
        this.searched = this.artists.filter(element =>{
               return element.genre.includes(selected);
      });
    }
  },
  computed:{
    test(){
      return this.searched
    }
  }
}

</script>

<style lang="scss" scoped>
@import "../assets/style/partial/variables.scss";
.main{
  height: calc(100vh - $header-height);
  background-color: #1e2d3b;
  display: flex;
  flex-direction: column;
  align-items: center;



  .cards{
  width: 60%;
  height: 80%;
  padding: 20px 0;
  display: grid;
  gap: 40px;
  grid-template-columns: repeat(5,1fr);
  grid-template-rows: repeat(2,1fr);
  }
}
</style>