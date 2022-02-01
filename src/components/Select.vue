<template>
    <select @change="$emit('search', selected )" v-model="selected" 
    >
      <option value="" selected>Filter...</option>
      <option v-for="element,index in selectGenre" :key="index">
          {{element}}
      </option>
    </select>
</template>

<script>
export default {
    name: "Select",
    props:{
        info:Array
    },
    data () {
    return {
      selectGenre: [],
      selected:""
    }
  },
    methods:{
        populateSelect()
        {
            this.info.forEach((element) => {
                if(!this.selectGenre.includes(element.genre)){
                    this.selectGenre.push(element.genre)
                }
            });
        }
    },
    watch:{
        info: function(){
            this.populateSelect()
        }
    }
    
}
</script>

<style lang="scss" scoped>
  select{
    margin-top: 10px;
    padding: 5px 5px;
    border: none;
    border-radius: 20px 20px;
    background-color: #2e3a46;
    width: 150px;
  }
</style>