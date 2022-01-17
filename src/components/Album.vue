<template>
  <div class="col card p-3 m-3">
      <img
      class="w-100"
      :src="src"
      :alt="author"
    >
    <h2 class="">
      {{ title }}
    </h2>
    <h3 class="fs-6 fw-normal">
      {{ author }}
    </h3>
    <h4 class="fs-5">
      {{ year }}
    </h4>
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