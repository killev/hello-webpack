<template>
  <div>
    <img :src="items[image].image" class="first-image">
    <img :src="items2[image2].image" class="second-image">
    <img :src="items3[image3].image" class="third-image">
    <ul class="first-image-list">
      <li v-for="(item, key) in items" class="first-list-elements">
        <span @click="image = key"><img :src="item.image"/></span>
      </li>
    </ul>
    <ul class="second-image-list">
      <li v-for="(item, key) in items2" class="second-list-elements">
        <span @click="image2 = key"><img :src="item.image"/></span>
      </li>
    </ul>
    <ul class="third-image-list">
      <li v-for="(item, key) in items3" class="third-list-elements">
        <span @click="image3 = key"><img :src="item.image"/></span>
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

    let initImg3 = "bla9"
      if (this.$router.currentRoute.query.image3 != undefined) {
       initImg3 = this.$router.currentRoute.query.image3 
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
      image3: initImg3,
      items3: {
        "bla9": { image: require('@/assets/Olimpic.png') },
        "bla10": { image: require('@/assets/Chorno.jpg') },
        "bla11": { image: require('@/assets/Desna.jpg') },
        "bla12": { image: require('@/assets/Arsenal.png') },
      }
    }
  }, 
  computed: {
    combined: function(){
      return { image: this.image, image2: this.image2, image3: this.image3 }
    }
  },
  watch: {
    combined: function(val){
      this.$router.push({ query: { image: val.image, image2: val.image2, image3: val.image3 }})
    }
  }
}
</script>

<style>
.first-image {
    width: 500px;
    height: 500px;
    opacity: 0.2;
}
.second-image {
    width: 500px;
    height: 500px;
    opacity: 0.2;  
    margin-left: 300px;
}
.third-image {
    width: 500px;
    height: 500px;
    opacity: 0.2;
}
.first-image-list{
  list-style-type: none;
}
.first-list-elements {
  display: inline;
  margin-left: 10px;
}
.second-image-list {
    list-style-type: none;
}
.second-list-elements {
  display: inline;
  margin-left: 10px;
}
.third-image-list{
  list-style-type: none;
}
.third-list-elements {
  margin-left: 10px;
  display: inline;
}
</style>

