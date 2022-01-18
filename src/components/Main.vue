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
      <select id="select" 
              class="form-select" 
              aria-label="Default select example">
        <option selected>Seleziona il tuo genere preferito</option>
        <option value="rock">Rock</option>
        <option value="pop">Pop</option>
        <option value="jazz">Jazz</option>
        <option value="metal">Metal</option>
      </select>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Album from "./Album.vue";

export default {
  name: "Main",
  components:{
    Album,
  },
  data() {
    return {
      album: null,
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
};
</script>

<style lang="scss">

</style>
