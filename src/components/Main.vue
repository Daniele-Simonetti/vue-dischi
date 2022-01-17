<template>
  <main>
    <div
      v-if="discs"
      class="container"
    >
      <div
        v-for="(disc, index) in discs"
        :key="index"
        class="card"
      >
        <img
          :src="disc.poster"
          :alt="disc.title"
        >
        <h2 class="fs-5 fw-bold mt-3 mb-4">
          {{ disc.title }}
        </h2>
        <h3>{{ disc.author }}</h3>
        <h4>{{ disc.year }}</h4>
      </div>
    </div>
  </main>
</template>

<script>
// installo axios e lo importo per poi prendere i data
import axios from 'axios';
// tengo un esempio dell'array che prendo nei data per comodità
//  "response": [
//    {
//      "poster": "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg",
//      "title": "New Jersey",
//      "author": "Bon Jovi",
//      "genre": "Rock",
//      "year": "1988"
//     },

export default {
  name: 'Main',
  data() {
    return {
      discs: null,
    };
  },
  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then((result) => {
        console.log(result.data.response);
        this.discs = result.data.response;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style lang="scss">
  main {
    background-color: #1E2D3B;
    padding: 3em;
    .container {
      height: 100%;
      display: flex;
      flex-wrap: wrap;
      .card {
        flex-basis: calc((100% / 5) - 2em);
        margin: 1em;
        background-color: #2E3A46;
        padding: 1em;
        h2 {
          color: white;
          text-transform: uppercase;
        }
      }
    }
  }
</style>
