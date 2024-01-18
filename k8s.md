kubectl create configmap eip4844-devnet-config \
  --from-file=geth/geth.sh \
  --from-file=geth/jwtsecret \
  --from-file=geth/genesis.json \
  --from-file=geth/enodes.list

kubectl patch configmap eip4844-devnet-config \
  --patch "{\"data\": {$(cat .env | grep -v '^#' | sed 's/^/\"/;s/=/\":\"/;s/$/\"/' | awk '{if (NR != 1) {print l","} l=$0} END {print l}') }}"


kubectl apply -f .