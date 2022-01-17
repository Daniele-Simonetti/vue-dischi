<template>
  <div
    class="card"
  >
    <img
      :src="image"
      :alt="title"
    >
    <h2 class="fs-5 fw-bold mt-3 mb-4">
      {{ title }}
    </h2>
    <h3>{{ author }}</h3>
    <h4>{{ year }}</h4>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: [
    'image',
    'title',
    'author',
    'year',
  ],
};
</script>

<style lang="scss" scoped>

</style>
