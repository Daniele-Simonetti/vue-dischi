<template>
  <div
    class="card col"
  >
    <img
      :src="image"
      :alt="imageAlt"
    >
    <h2 class="fs-5 fw-bold mt-3 mb-4">
      {{ mainHeading }}
    </h2>
    <h3 class="fs-6">
      {{ heading3 }}
    </h3>
    <h4 class="fs-6">
      {{ heading4 }}
    </h4>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    image: {
      type: String,
      required: true,
    },
    imageAlt: {
      type: String,
      required: true,
    },
    mainHeading: {
      type: String,
      required: true,
    },
    heading3: {
      type: String,
      required: true,
    },
    heading4: {
      type: String,
      required: true,
    },
    genere: {
      type: String,
      default: null,
    },
  },
};
</script>

<style lang="scss" scoped>
.card {
  flex-basis: calc((100% / 5) - 2em);
  margin: 1em;
  background-color: #2E3A46;
  padding: 1.1em;
  h2 {
    color: white;
    text-transform: uppercase;
  }
  h3, h4 {
    color: gray;
  }
}

</style>
