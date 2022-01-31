<template>
      <div class="card">
        <img :src="info.poster" alt="">
        <span class="title">{{info.title}}</span>
        <div>
          <span class="artist">{{info.author}}</span>
          <span class="year">{{info.year}}</span>
        </div>
      </div>
</template>

<script>
export default {
    name: "Cards",
    props:{
      info:Object
    }
}
</script>

<style lang="scss" scoped>

  .card{
    padding: 20px 0;
    background-color: #2e3a46;
    display: flex;
    flex-direction: column;
    text-align: center;
    gap: 10px;
    
    img{
      border: 1px solid white;
      margin: 0 auto;
      width: 85%;
      height: 180px;
      object-fit: cover;
      object-position: top;
    }

    .title{
      font-size: 22px;
      font-weight: bold;
      text-transform: uppercase;
      color: white;
      margin-bottom: 20px;
    }
    .artist{
      font-size: 17px;
      color: grey;
      display: block;
    }
    .year{
      font-size: 15px;
      color: grey;
    }
  }

</style>