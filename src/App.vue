<script setup>
import { KeyPair } from "near-api-js";
import HelloWorld from './components/HelloWorld.vue'
import { Wallet } from "./near-wallet";
import {Contract} from './near-interface'
// import { WatchEffect } from "vue";
const CONTRACT_ID = "nft1.actionhup.testnet";
console.log(KeyPair.fromRandom("ed25519"))
</script>

<template>
 
  <button @click = "signin">
    hello
  </button>
</template>


<script>
  export default {
        data() {
            return {
                counter: 0
            }
        },
        methods: {
            async signin() {
              const new_wallet =  new Wallet({createAccessKeyFor: "nft1.actionhup.testnet"})
              const contract = new Contract({contractId: "nft1.actionhup.testnet", walletTouse: new_wallet})
              await new_wallet.startUp();
              new_wallet.signIn();
            }
          
        }
    }
</script>


<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
