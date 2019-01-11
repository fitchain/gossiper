# Fitchain gossiper network

TODO: provide motivation and high level description


# Getting started

## Start node 1

Start first node on ```127.0.0.1:42000``` opening RPC on default port ```4242``` and connect this node to ethereum account provided by keyfile

``` python server.py -i 127.0.0.1 -p 42000 --rpc -k data/keyfile--3d4a8e640bdcf0c640ea42e5c25877afc572101c ```


## Start node 2 (with bootstrap from node 1)

Start second node listening to ```127.0.0.1:43000``` connected to bootstrap node at ```127.0.0.1:42000``` opening RPC on ```4343``` and connect to another ethereum account

``` python server.py -b 127.0.0.1:42000 -p 43000 --rpc --rpcport 4343 -k data/keyfile--40210576d9262a214aac7494e85718ec3a12ec54 ```


## Creating transaction via RPC

```POST Request```
```curl -X POST --data '{"jsonrpc":"1.0","method":"fit_sendTransaction","params":["42","43","44"],"id":67}' 127.0.0.1:4242```

`curl -H "Content-Type: application/json" -X POST -d '{"jsonrpc":"2.0","method":"fit_sendTransaction", "params": {"model_id":"42", "accuracy":"0.43", "error":"0.84", "eot": 1}, "id":67}' 127.0.0.1:4242`

`curl -H "Content-Type: application/json" -X POST -d '{"jsonrpc":"2.0","method":"fit_getData", "params": "474630524e2b4b756d6268586b4a6a726f61564a41304e6d4d46493d", "id":67}' 127.0.0.1:4242`


while true; do curl -H "Content-Type: application/json" -X POST -d '{"jsonrpc":"2.0","method":"fit_sendTransaction", "params": {"model_id":"42", "accuracy":"0.43", "error":"0.84", "eot": 1}, "id":67}' 127.0.0.1:4242; done >> /dev/null
