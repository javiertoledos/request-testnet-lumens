<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-md-8 mx-auto">
          <h1>Get Stellar Lumens from Testnet</h1>
          <p>
            This is a very simple client to get lumens from the Stellar testnet. To use it, paste a
            public key you own or generate a new address. Make sure to save the private address
            when requesting lumens. The data is generated in your browser, this means that the generated
            private key is not sent to any server.
          </p>
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
