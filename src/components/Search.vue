<template>
  <div>
      <select 
        id="select" 
        class="form-select" 
        aria-label="Default select example"
        v-model="inputValue"
        @change="$emit('searchAlbum', inputValue)">
          <option selected>Seleziona il tuo genere preferito</option>
          <option value="Rock">Rock</option>
          <option value="Pop">Pop</option>
          <option value="Jazz">Jazz</option>
          <option value="Metal">Metal</option>
      </select>
  </div>
</template>

<script>
export default {
    name: 'Search',
    data() {
        return {
            inputValue: '',
        }
    },
}
</script>

<style>

</style>