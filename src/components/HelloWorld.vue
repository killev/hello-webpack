<template>
  <div>
  <img :src="items[image].image" id="test">
  <ul id="ul"> 
  <li v-for="(item, key) in items" id="li">
    <span @click="image = key"><img :src="item.image"/></span>
  </li>
</ul>
</div>    
</template>
  
<script>
import Router from '../router';
export default{
  name: 'app',
  data: function() { 
    let initImg = "bla1"
    if (this.$router.currentRoute.query.image != undefined) {
       initImg = Router.currentRoute.query.image 
    }
    return {
    image: initImg,
    items: {
     "bla1": { image: require('@/assets/Kar.jpg') },
     "bla2": { image: require('@/assets/DK.jpg') },
     "bla3": { image: require('@/assets/Lviv.jpg') },
     "bla4": { image: require('@/assets/Shakhtar.jpg') },
     "bla5": { image: require('@/assets/Vorskla.png') },
     "bla6": { image: require('@/assets/Mariupol.gif') },
     "bla7": { image: require('@/assets/Zorya.png') },
     "bla8": { image: require('@/assets/Olexa.jpg'), },
    }
  }},
  watch: {
    image: value => {
      Router.push({ query: { image: value }})
    }
  }
}
</script>

<style>
#test {
    width: 500px;
    height: 500px;
    opacity: 0.2;
}
#ul{
  list-style-type: none;
  /* display: inline-block; */
}
#li {
  display: inline;
  margin-left: 10px;
}
</style>

