<template>
  <main>
    <div
      v-if="discs"
      class="container"
    >
      <div class="row">
        <Select
          @selectGen="filtering($event)"
        />
      </div>
      <div class="row row-col-5">
        <Card
          v-for="(disco, index) in newDiscs"
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
import Select from './Select.vue';

export default {
  name: 'Main',
  components: {
    Card,
    Select,
  },
  data() {
    return {
      discs: null,
      newDiscs: null,
      selectedDiscs: 'All',
    };
  },
  computed: {
  },
  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then((result) => {
        // creo due array uguali per ripopolare l'array dopo il filtro
        this.discs = result.data.response;
        this.newDiscs = result.data.response;
      })
      .catch((error) => {
        console.log(error);
      });
  },
  methods: {
    // filterDisc() {
    //   // metto i due array uguali così quando sono su all non parte il filtro
    //   this.discs = this.newDiscs;
    //   // se il mio v-model è diverso da 'All? allora faccio partire il filtro
    //   if (this.selectedDiscs !== 'All') {
    //     this.discs = this.discs.filter((element) => {
    //       if (element.genre.includes(this.selectedDiscs)) {
    //         return true;
    //       }
    //       return false;
    //     });
    //   }
    // },
    filtering(opt) {
      console.log(opt);
      // inverto i due array per usare la copia del mio array principale
      this.selectedDiscs = opt;
      this.newDiscs = this.discs;
      if (opt !== 'All') {
        this.newDiscs = this.discs.filter((element) => {
          if (element.genre.includes(opt)) {
            return true;
          }
          return false;
        });
      }
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
