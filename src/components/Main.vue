<template>
  <main>
    <div class="container">
      <div class="card">
        <img src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="">
        <h1>New jersey</h1>
        <h3>Bon jovi</h3>
        <h4>1988</h4>
      </div>
    </div>
  </main>
</template>

<script>
// installo axios e lo importo per poi prendere i data
import axios from 'axios';
// tengo un esempio dell'array che prendo nei data per comodità
//  "response": [
//         {
//             "poster": "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg",
//             "title": "New Jersey",
//             "author": "Bon Jovi",
//             "genre": "Rock",
//             "year": "1988"
//         },

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
        console.log(result);
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
    height: 100%;
    .container {
      background-color: red;
      height: 100%;
      display: flex;
      flex-wrap: wrap;
      .card {
        flex-basis: calc((100% / 5) - 2em);
        margin: 1em;
      }
    }
  }
</style>
