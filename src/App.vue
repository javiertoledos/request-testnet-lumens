<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-md-6 mx-auto">
          <request-lumens-form />
        </div>
      </div>
    </div>

  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import RequestLumensForm from './components/RequestLumensForm.vue';

@Component({
  components: {
      RequestLumensForm,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap.scss";
</style>
