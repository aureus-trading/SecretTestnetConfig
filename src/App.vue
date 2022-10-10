<template>
  <div class="content">
    <h1>Step 1: Check if Pulsar has already been added</h1>
    <p>
      If you already have Pulsar or Testnet configured in Keplr you will
      need to remove it first, or this tool will do nothing.
    </p>

    <ol class="guide">
      <li>
        Open and unlock Keplr, then click the name of the currently selected
        chain at the top
      </li>
      <img alt="Vue logo" src="./assets/chainname.png" />
      <li>
        Scroll to the bottom, and check Pulsar or Testnet are not listed
        under Beta Support
      </li>
      <img alt="Vue logo" src="./assets/betasupport.png" />
      <li>If they are, click the X next to the chain name to remove it</li>
    </ol>
    
    <h1>Step 2: Add Pulsar to Keplr</h1>

    <ol class="guide">
      <li>Open and unlock Keplr.</li>

      <li>
        Click the add button below. If nothing happens it means that you already
        have a Pulsar chain installed. Either use it, or follow the
        instructions in Step 1 to remove it.
      </li>

      <button class="button" @click="addNetwork()">Add Pulsar</button>

      <li>Keplr will open an approval window. Read it, then click Approve</li>

      <img alt="Vue logo" src="./assets/keplrapprove.png" />

      <li>
        If no error appears then Pulsar was successfully added to Keplr.
      </li>
    </ol>

    <h1>Step 3: Switch from Mainnet to Pulsar in Keplr</h1>

    <ol class="guide">
      <li>
        Open and unlock Keplr, then click the name of the currently selected
        chain at the top
      </li>
      <img alt="Vue logo" src="./assets/chainname.png" />
      <li>
        Scroll to the bottom then click Secure Secrets Pulsar under Beta Support
      </li>
      <img alt="Vue logo" src="./assets/securesecretsconnect.png" />
      <li>
        Congrats! Keplr is now using the Secret Network Pulsar testnet
        chain via Secure Secrets
      </li>
    </ol>
    <br />

  </div>
</template>

<script>
export default {
  methods: {
    addNetwork() {
      window.keplr.experimentalSuggestChain({
        chainId   : "secretdev-1",
        chainName : "SecureSecrets Dev",
        rpc       : "https://rpc.localdocker.securesecrets.org/",
        rest      : "https://api.localdocker.securesecrets.org/",
        bip44     : {
          coinType : 529,
        },
        coinType      : 529,
        stakeCurrency : {
          coinDenom        : "SCRT",
          coinMinimalDenom : "uscrt",
          coinDecimals     : 6,
        },
        bech32Config : {
          bech32PrefixAccAddr  : "secret",
          bech32PrefixAccPub   : "secretpub",
          bech32PrefixValAddr  : "secretvaloper",
          bech32PrefixValPub   : "secretvaloperpub",
          bech32PrefixConsAddr : "secretvalcons",
          bech32PrefixConsPub  : "secretvalconspub",
        },
        currencies : [ {
          coinDenom        : "SCRT",
          coinMinimalDenom : "uscrt",
          coinDecimals     : 6,
        } ],
        feeCurrencies : [ {
          coinDenom        : "SCRT",
          coinMinimalDenom : "uscrt",
          coinDecimals     : 6,
        } ],
        gasPriceStep : {
          low     : 0.1,
          average : 0.25,
          high    : 0.4,
        },
        features : [ "secretwasm" ],
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#app .content {
  width: 800px;
  margin: 0 auto;
}

ol.guide li {
  padding: 1em 0;
}

h3 {
  margin: 40px 0 0;
}

a {
  color: #42b983;
}
</style>
