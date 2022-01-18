<template>
  <main>
    <div
      v-if="discs"
      class="container"
    >
      <div class="row">
        <div class="col-12 select">
          <select
            v-model="selectedDiscs"
            class="form-select form-select-lg mb-3"
            aria-label=".form-select-lg example"
            @change="filterDisc()"
          >
            <option
              value="All"
            >
              All
            </option>
            <!-- rock, pop,jazz, metal  -->
            <option value="Rock">
              Rock
            </option>
            <option value="Pop">
              Pop
            </option>
            <option value="Jazz">
              Jazz
            </option>
            <option value="Metal">
              Metal
            </option>
          </select>
        </div>
      </div>
      <div class="row row-col-5">
        <Card
          v-for="(disco, index) in selectedDiscs"
          :key="index"
          :image="disco.poster"
          :image-alt="disco.title"
          :main-heading="disco.title"
          :heading3="disco.author"
          :heading4="disco.year"
        />
      </div>
    </div>
  </main>
</template>

<script>
// installo axios e lo importo per poi prendere i data
import axios from 'axios';
import Card from './Card.vue';

export default {
  name: 'Main',
  components: {
    Card,
  },
  data() {
    return {
      discs: null,
      genre: 'All',
      selectedDiscs: null,
    };
  },
  computed: {
    // initialDiscs() {
    //   if (this.selectedDiscs === 'All') {
    //     return this.discs;
    //   }
    //   return false;
    // },
  },
  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then((result) => {
        // console.log(result.data.response);
        this.discs = result.data.response;
      })
      .catch((error) => {
        console.log(error);
      });
  },
  methods: {
    filterDisc() {
      this.genre = this.selectedDiscs;
      console.log('selectedDisc', this.selectedDiscs);
      console.log('genre', this.genre);
      // console.log(this.genre);
      this.selectedDiscs = this.discs.filter((element) => {
        if (element.genre === this.selectedDiscs) {
          return true;
        } if (this.selectedDiscs === 'All') {
          return this.discs;
        }
        return false;
      });
      // return this.genre.filter(
      //   (element) => element.genre.includes(this.selectedDiscs),
      // );
      // element.genre === this.selectedDiscs
    },
  },
};
</script>

<style lang="scss">
  main {
    background-color: #1E2D3B;
    padding: 3em;
    height: 100vh;
    .select {
      color: black;
    }
  }
</style>
