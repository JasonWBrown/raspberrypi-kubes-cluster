# Cardano Node Spec

# Spin up the Node using PVC and NODE Affinity.

1. Prep the HOST node by ensuring the directory for the persistent volume exists. 
1. If you set up kubes correctly you should be able to run kubes from your local machine.
   ```
   > kubectl apply -f ./deployment/testnet-relay.yaml
   ```