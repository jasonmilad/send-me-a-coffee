<script>
  import { ethers } from 'ethers';
async function sendEth() {
  if(typeof(window.ethereum)!== 'undefined'){
    const provider = new ethers.providers.Web3Provider(window.ethereum);
    const signer = await provider.getSigner();
    await signer.sendTransaction({to:"0x2E544A74a4b2FabB22f05437E6cb1c2Fc53e3FeA", value: amount});
}
}
let amount = 0;
let clicked = false;
</script>

<main>
<h1>Hi, I'm Jason, a student and web3 developer</h1>
<input bind:value={amount} type="number" min="0" placeholder="0">
<button id = "buy" on:click={()=> {clicked=true}}>Buy me a coffee</button>
</main>
{#if clicked}
<div class = "wallets">
  <div class="header"><span>Please choose your wallet</span>
  <button class="exit" on:click={()=>{clicked=false}}>x</button></div>
  <button class="wallet" on:click={sendEth}> <img src="https://upload.wikimedia.org/wikipedia/commons/3/36/MetaMask_Fox.svg"/> Metamask</button>
  <button class = "wallet" on:click={sendEth}> <img src="https://is1-ssl.mzstatic.com/image/thumb/Purple112/v4/97/96/7c/97967ca2-48c5-5005-44be-6d09157a7633/AppIcon-0-0-1x_U007emarketing-0-0-0-10-0-0-sRGB-0-0-0-GLES2_U002c0-512MB-85-220-0-0.png/1024x1024.jpg"/> Coinbase wallet</button>
</div>
{/if}

<style>


.exit {
  display: inline;
}

.wallets {
  position: absolute;
  top: 50vh;
  left: 50vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}
img {
  width: 30%;
  height: 30%;
}
.wallet {
  display: flex;
  align-items: center;
  width:30%;
  height: 30%;
  gap: 1rem;
}
input {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 500;
  font-family: inherit;
  background-color: #1a1a1a;
  transition: border-color 0.25s;
}
input:hover {
  border-color: #646cff;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
input[type=number] {
  -moz-appearance: textfield;
}

</style>