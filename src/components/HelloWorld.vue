<template>
  <div>
  <img :src="items[image].image" id="test">
  <img :src="items2[image2].image" id="test2">
  <ul id="ul">
  <li v-for="(item, key) in items" id="li">
    <span @click="image = key"><img :src="item.image"/></span>
  </li>
  </ul>
  <ul id="ul2">
  <li v-for="(item, key) in items2" id="li2">
    <span @click="image2 = key"><img :src="item.image"/></span>
  </li>
  </ul>
</div>    
</template>
  
<script>

export default {
  name: 'app',
  data: function() { 
    let initImg = "bla1"
    if (this.$router.currentRoute.query.image != undefined) {
       initImg = this.$router.currentRoute.query.image 
    }

    let initImg2 = "bla5"
      if (this.$router.currentRoute.query.image2 != undefined) {
       initImg2 = this.$router.currentRoute.query.image2 
    }

    return {
      image: initImg,
      items: {
        "bla1": { image: require('@/assets/Kar.jpg') },
        "bla2": { image: require('@/assets/DK.jpg') },
        "bla3": { image: require('@/assets/Lviv.jpg') },
        "bla4": { image: require('@/assets/Shakhtar.jpg') },
      },
      image2: initImg2,
      items2: {
        "bla5": { image: require('@/assets/Vorskla.png') },
        "bla6": { image: require('@/assets/Mariupol.gif') },
        "bla7": { image: require('@/assets/Zorya.png') },
        "bla8": { image: require('@/assets/Olexa.jpg'), },
      },
    }
  }, 
  computed: {
    combined: function(){
      return { image: this.image, image2: this.image2 }
    }
  },
  watch: {
    combined: function(val){
      this.$router.push({ query: { image: val.image, image2: val.image2 }})
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
#test2 {
    width: 500px;
    height: 500px;
    opacity: 0.2;  
    margin-left: 300px;
}
#ul{
  list-style-type: none;
}
#li {
  display: inline;
  margin-left: 10px;
}
#ul2 {
    list-style-type: none;
}
#li2 {
  float: right;
}
</style>

