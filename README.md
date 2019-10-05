Minimal Node.js application for intro to Docker tutorial: https://www.digitalocean.com/community/tutorials/how-to-build-a-node-js-application-with-docker

## Pull image from github registry

### Create Credential in Kubernetes
```
kubectl create secret docker-registry regcred \
--docker-server=docker.pkg.github.com/<username>/ \
--docker-username=<username> \
--docker-password=<personal access tokens> \
--docker-email=<user email>
```

### Update Kubernetes descriptor
```
    spec:
      containers:
      - name: nodejs
        image: docker.pkg.github.com/<username>/istio-sample/app:1.0
        ports:
        - containerPort: 8080
      imagePullSecrets:
         - name: regcred
```


## References
[How To Install and Use Istio With Kubernetes](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-istio-with-kubernetes#step-2-%E2%80%94-installing-istio-with-helm)
