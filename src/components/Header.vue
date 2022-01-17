<template>
  <header>
    <div class="container-fluid">
      <div class="row">
        <div class="col">
        <i class="fab fa-spotify"></i>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
};
</script>

<style lang="scss" scoped>
header {
  background-color: #2E3A46;
  height: 100px;
  i {
    width: 4%;
    background-color: green;
  }
}

</style>
