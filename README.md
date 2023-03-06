_____________________________

Snapshots are taken automatically every 6 hours starting at 00:00 UTC
<br/>pruning: 100/0/19 | indexer: null | version tag: v0.19.2

_____________________________
- RPC : https://rpc.nolus.devononft.com
- gRPC : https://grpc.nolus.devononft.com
- API : https://api.nolus.devononft.com
- Snapshots : https://snapshot.nolus.devononft.com
_____________________________

## Instructions
#### Stop the service and reset the data
```
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```

#### Download latest snapshot
```
curl -L https://snapshot.nolus.devononft.com/nolus/snapshot_latest.tar.lz4 | tar -Ilz4 -xf - -C $HOME/.nolus
```

#### Move File
```
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
```

#### Restart Nolus Node
```
sudo systemctl start nolusd
```

#### Check the log
```
sudo journalctl -u nolus -f --no-hostname -o cat
```
