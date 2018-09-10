<template>
    <div>
        <h2>Request</h2>
        <form @submit.prevent="requestFunds">
            <div class="form-group">
                <button @click.prevent="createPair" class="btn btn-outline-secondary">
                    Generate Public/Private keys
                </button>
                <p class="my-3">- or -</p>
                <label for="publicKey">Paste your public key</label>
                <input type="text" v-model="publicKey" @change="clearPrivateKey" class="form-control" id="publicKey" />
            </div>
            <div class="form-group" v-show="privateKey">
                <label for="privateKey">Private Key</label>
                <input type="text" v-model="privateKey" class="form-control" id="privateKey" readonly />
                <small>Make sure to save your private key</small>
            </div>
            <button type="submit" class="btn btn-primary">Request</button>
        </form>
        <div v-show="requestMsg.text" class="my-3   alert" :class="'alert-' + requestMsg.type">
            {{ requestMsg.text }}
        </div>
    </div>
</template>

<script lang="ts">
    import { Component, Prop, Vue } from 'vue-property-decorator';
    import StellarSdk from 'stellar-sdk';
    import axios from 'axios';

    @Component
    export default class RequestLumensForm extends Vue {
        private publicKey = '';
        private privateKey = '';

        private requestMsg = {
            type: 'light',
            text: '',
        };

        private async requestFunds() {
            try {
                const {data} = await axios.get('https://friendbot.stellar.org', {
                    params: {
                        addr: this.publicKey
                    }
                });

                this.requestMsg.type = 'success';
                this.requestMsg.text = 'Lumens requested!'
            } catch(e) {
                this.requestMsg.type = 'success';
                this.requestMsg.text = e.toString();
            }




        }

        private createPair() {
            const pair = StellarSdk.Keypair.random();

            this.publicKey = pair.publicKey();
            this.privateKey = pair.secret();
        }

        private clearPrivateKey() {
            this.privateKey = '';
        }
    }
</script>