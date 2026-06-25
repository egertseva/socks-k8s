# socks-k8s
k8s manifests to deploy socks proxy

Steps to use socks proxy in k8s:
1. Generate an ssh private key and save it on your proxy server.
   Create a secret in k8s that contains it:
   kubectl create secret generic socks-priv-key --from-file=ssh-privatekey=~/.ssh/id_rsa
   
2. Create a secret that stores your known-hosts:
   kubectl create secret generic known-hosts --from-file=known-hosts=~/.ssh/known_hosts

3. Fill in your server's address in the command in deployment manifest.

4. Deploy k8s manifests and make requests via socks5://socks-service.socks:80.
   
