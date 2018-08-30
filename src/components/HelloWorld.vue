<template>
  <div>
  <img :src="items[image].image" id="test">
  <ul id="ul"> 
  <li v-for="(item, key) in items">
    <span @click="image = key"><img :src="item.image"/></span>
  </li>
</ul>
</div>    
</template>
  
<script>
import Router from '../router';
export default{
  name: 'app',
  data: ()=> { 
    let initImg = "bla1"
    if (Router.currentRoute.query.image != undefined) {
       initImg = Router.currentRoute.query.image 
    }
    return {
    image: initImg,
    items: {
     "bla1": { image: require('@/assets/Kar.jpg') },
     "bla2": { image: require('@/assets/DK.jpg') },
     "bla3": { image: require('@/assets/Lviv.jpg') },
     "bla4": { image: require('@/assets/Shakhtar.jpg') },
    }
  }},
  watch: {
    // eslint-disable-next-line
    image: value => {
      Router.push({ query: { image: value }})
    }
  }
}
</script>

