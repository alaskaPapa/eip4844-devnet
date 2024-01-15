kubectl create configmap eip4844-devnet-config \
  --from-file=geth/geth.sh \
  --from-file=geth/jwtsecret \
  --from-file=geth/genesis.json \
  --from-file=geth/enodes.list

kubectl apply -f .