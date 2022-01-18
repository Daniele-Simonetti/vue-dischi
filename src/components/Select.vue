<template>
  <div class="col-12 select">
    <select
      v-model="selected"
      class="form-select form-select-lg mb-3"
      aria-label=".form-select-lg example"
      @change="$emit('selectGen', selected)"
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
</template>

<script>
export default {
  name: 'Select',
  data() {
    return {
      selected: 'All',
    };
  },
};
</script>

<style>

</style>
