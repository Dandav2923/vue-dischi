<template>
  <div class="col card p-3 m-3 text-center">
      <img
      class="w-100"
      :src="src"
      :alt="author"
    >
    <h2 class="fs-4 text-uppercase text-center mt-2">
      {{ title }}
    </h2>
    <h3 class="fs-6">
      {{ author }}
    </h3>
    <span class="fs-6">
      {{ year }}
    </span>
  </div>
</template>

<script>
export default {
    name: 'Album',
    props: [
        'src',
        'title',
        'author',
        'year'
    ]
}
</script>

<style>

</style>