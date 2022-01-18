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
        @searchAlbum="filteredAlbum($event)"
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
      filteredGenre:[],
      // selectValue:'',
    }
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.album = response.data.response;
        this.filteredGenre = response.data.response;
        // console.log(response.data.response);
      })
      .catch((error) => {
        console.log(error);
        });
  },
  methods: {
    filteredAlbum(inputValue){
      this.album = this.filteredGenre;
      // this.selectValue = inputValue;
      if(inputValue == 'selected' ){
        return this.album
      }
      else if (inputValue == 'Rock') {
        return this.album =  this.album.filter((element) => element.genre == 'Rock');
      }
      else if (inputValue == 'Pop') {
        return this.album = this.album.filter((element) => element.genre == 'Pop');
      }
      else if (inputValue == 'Jazz') {
        return this.album = this.album.filter((element) => element.genre == 'Jazz');
      }
      else if (inputValue == 'Metal') {
        return this.album = this.album.filter((element) => element.genre == 'Metal');
      }
    }
  },
  // computed:{
    // filteredAlbum(text){
    //   this.album.filter((element) => console.log(element.genre));
    //   console.log(text);
    //   }
  //   filteredAlbum(){
  //     if(this.filteredGenre == 'selected' ){
  //       return this.album
  //     }
  //     else if (this.filteredGenre == 'Rock') {
  //       return this.album =  this.album.filter((element) => element.genre == 'Rock');
  //     }
  //     else if (this.filteredGenre == 'Pop') {
  //       return this.album = this.album.filter((element) => element.genre == 'Pop');
  //     }
  //     else if (this.filteredGenre == 'Jazz') {
  //       return this.album = this.album.filter((element) => element.genre == 'Jazz');
  //     }
  //     else if (this.filteredGenre == 'Metal') {
  //       return this.album = this.album.filter((element) => element.genre == 'Metal');
  //     }
  //   }
  // },
};
</script>

<style lang="scss">

</style>
