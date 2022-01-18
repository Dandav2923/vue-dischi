<template>
  <div class="container bg-red">
    <div class=" row row-cols-6 justify-content-around">
        <Album 
          v-for="(element, index) in album"
          :key="index"
          :src="element.poster"
          :author="element.author"
          :title="element.title"
          :year="element.year"
        />
    </div>
    <div class="row p-4">
      <Search 
        @searchAlbum="searchAlbumFilter($event.target.value)"
         />
      <!-- <select 
        id="select" 
        class="form-select" 
        aria-label="Default select example">
          <option selected>Seleziona il tuo genere preferito</option>
          <option value="rock">Rock</option>
          <option value="pop">Pop</option>
          <option value="jazz">Jazz</option>
          <option value="metal">Metal</option>
      </select> -->
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Album from "./Album.vue";
import Search from "./Search.vue"

export default {
  name: "Main",
  components:{
    Album,
    Search,
  },
  data() {
    return {
      album: null,
      filteredGenre:'',
    }
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.album = response.data.response;
        console.log(response.data.response);
      })
      .catch((error) => {
        console.log(error);
        });
  },
  methods: {
    searchAlbumFilter(inputValue) {
      this.filteredGenre = inputValue;
    },
    filteredArray(){
      console.log('1');
      // if(this.filteredGenre == 'selected' ){
      //   return this.album
      // }
      // else if (this.filteredGenre == 'rock') {
      //   return this.album.filter((element) => element.genre == 'Rock');
      // }
      // else if (this.filteredGenre == 'pop') {
      //   return this.album.filter((element) => element.genre == 'Pop');
      // }
      // else if (this.filteredGenre == 'jazz') {
      //   return this.album.filter((element) => element.genre == 'Jazz');
      // }
      // else if (this.filteredGenre == 'metal') {
      //   return this.album.filter((element) => element.genre == 'Metal');
      // }
    }
  },
  // computed:{
  //   filteredArray(event){
  //     console.log(event.target.value);
  //     // if(this.filteredGenre == 'selected' ){
  //     //   return this.album
  //     // }
  //     // else if (this.filteredGenre == 'rock') {
  //     //   return this.album.filter((element) => element.genre == 'Rock');
  //     // }
  //     // else if (this.filteredGenre == 'pop') {
  //     //   return this.album.filter((element) => element.genre == 'Pop');
  //     // }
  //     // else if (this.filteredGenre == 'jazz') {
  //     //   return this.album.filter((element) => element.genre == 'Jazz');
  //     // }
  //     // else if (this.filteredGenre == 'metal') {
  //     //   return this.album.filter((element) => element.genre == 'Metal');
  //     // }
  //   }
  // },
};
</script>

<style lang="scss">

</style>
