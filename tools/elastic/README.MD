To Generate the kibana-sealed.yaml run the following:
brew install kubectl
brew install kubeseal

kubectl create secret generic kibana-secret-setting --dry-run=client --from-literal=xpack.security.encryptionKey=$(openssl rand -hex 32) -o yaml  | /usr/local/Cellar/kubeseal/0.16.0/bin/kubeseal --controller-namespace flux-system --controller-name sealed-secrets -n elastic -o yaml > kibana-sealed.yaml