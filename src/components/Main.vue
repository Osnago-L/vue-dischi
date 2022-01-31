<template>
  <div class="main">
    <div class="cards">
    <Cards
      v-for="element,index in artists"
      :key="index"
      :info="element"
    />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Cards from './Cards.vue'

export default {
    name: "Main",
    components: {
    Cards
    },
  data () {
    return {
      artists: [],
    }
  },
  created: function(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
          .then((result)=> {
            // handle success
            this.artists = result.data.response;
            console.log(result.data.response);
          })
          .catch(function (error) {
            // handle error
            console.log(error);
          })
          .then(function () {
            // always executed
          });
      }
}

</script>

<style lang="scss" scoped>
@import "../assets/style/partial/variables.scss";
.main{
  height: calc(100vh - $header-height);
  background-color: #1e2d3b;
  display: flex;
  justify-content: center;

  .cards{
  width: 60%;
  height: 80%;
  padding: 40px 0;
  display: grid;
  gap: 40px;
  grid-template-columns: repeat(5,1fr);
  grid-template-rows: repeat(2,1fr);
  }
}
</style>