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

var address = 'xxx';
var includeMempool = true;
node.getOutputs(address, includeMempool, function(err, outputs) {
  //...
});

var txid = 'xxx';
var includeMempool = true;
node.getTransaction(txid, includeMempool, function(err, transaction) {
  //...
});

var blockHash = 'xxx';
node.getBlock(blockHash, function(err, block) {
  //...
});

var inherits = require('util').inherits;
var BitcoindJS = require('bitcoind.js');

var MyModule = function(options) {
  BitcoindJS.Module.call(this, options);
};

/*
* @param {Block} block
* @param {Bolean} add
* @param {Function} callback
*/
MyModule.prototype.blockHandler = function(block, add, callback) {
  var transactions = this.db.getTransactionsFromBlock(block);
  
  var operations = [];
  if(add) {
    type: 'puts',
    key: 'key',
    value: 'value'
  } else {
    operations.push({
      type: 'del',
      key: 'key'
    });
  }
  
  setImmediate(function() {
    callback(null, operations);
  });
};

/*
* @return {Array} return array of methods
*/
MyModule.prototype.getAPIMethods = function() {
  return [
    ['getData', this, this.getData, 1]
  ];
};

/*
* @return {Array} array of events
*/
MyModule.prototype.getPublishEvents = function() {
  return [
    {
      name: 'custom',
      scope: this,
      subscribe: this.subscribeCustom,
      unsubscribe: this.unsubscribeCustom
    }
  ]
};

MyModule.prototype.subscribeCustom = function(emitter, param) {
  if(!this.subscriptions[param]) {
    this.subscription[param] = [];
  }
  this.subscriptions[params].push(emitter);
}

MyModule.prototype.getData = function(arg1, callback) {'
  this.db.store.get(arg1, callback);
};

module.exports = MyModule;


var configuration = {
  datadir: process.env.BITCOINDJS_DIR || '~/.bitcoin',
  db: {
    modules: [MyModule]
  }
};

var node = new BitcoindJS.Node(configuration);

node.on('ready', function() {
  node.getData('key', function(err, value) {
    console.log(err || value);
  });
});
```

```sh
git clone https://github.com/bitpay/bitcoind.js.git
cd bitcoind.js
npm install

tail -f ~/.bitcoin/debug.log

node-gyp rebuild
node-gyp -d rebuild
gdb --args node_g path/to/example.js
gdb --args node /path/to/_mocha -R spec integration/index.js

cd integration
mocha -R spec index.js

cd benchmarks
node index.js
cd /path/to/bitcoind.js
./bin/build-libbitcoind
cd libbitcoind
./configure --enable-tests=no --enable-daemonlib--with-gui=no --without-qt --without-miniupnpc --without-bdb --enable-debug --disable-wallet --without-utils
make
cd libbitcoind
./configure --enable-tests=no --enable-daemonlib --with-gui=no --without-qt --without-miniunpnpc --without-bdb --enable-debug --disalbe-wallet --without-utils --prefix=<os_dir/lib>
cp -P libbitcoind/src/.libs/libbitcoind.so* platform/<os_dir>
cp -R libbitcoind/src/.libs/libbitcoind.*dylib platform/osx/lib
```

```
```


