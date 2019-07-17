### bitcoind.js
---
https://github.com/bitpay/bitcoind.js

```js
var BitcoinNode = require('bitcoind.js');

var configuration = {
  datadir: '~/.bitcoin',
  network: 'testnet'
};

var node = new BitcoinNode(configuration);

node.on('ready', function() {
  console.log('Bitcoin Node Ready');
});

node.on('error', function(err) {
  console.log(err);
});

node.on('addblock', function(block) {
  console.log('New Best Tip:', block.hash);
});

var address = 'xxx';
var includeMempool = true;
node.getUnspentOutputs(address, includeMempool, function(err, unspentOutputs) {
  //...
});

var address = 'xxx';
var includeMempool = true;
node.getBalance(address, includeMempool, function(err, balance) {
  //...
});






























```

```sh
git clone https://github.com/bitpay/bitcoind.js.git
cd bitcoind.js
npm install
```

```
```


