# Gitea and Drone in K8s
This repo conatins all artefacts, that are nessesarry to run gitea and drone together in kubernetes. While there exist helm charts out there, I had trouble using them together in a cluster. 

The artifacts in this repo work in different kubernetes clusters. 

## Install

1. Apply the `*.yml` files in the `gitea` directory. You may have to change the storage class in the `gitea-deployment.yml` file. 
2. Access `http://gitea` (This only works, if you use a wildcard domain, that is in your dns search suffix) and generate a oauth2 application with the url `http://drone/login`
3. Add the correct client id an client secret to the `drone-deployment.yml` file. Generate a shared secret on the command line with ` openssl rand -hex 16` and add it as the `DRONE_RPC_SECRET` to the `drone-deployment.yml` and the `drone-client.yml`
4. Create git repositories in gitea.
5. Apply all `*.yml` files in the `drone` subdirectory and access `http://drone` in your browser. 