# Learn ManageIQ


## Running in Docker

```
docker run -d -p 8443:443 manageiq/manageiq:petrosian-1
```


## Easy Install With Kubernetes

Step 1: Get the release templates
```
$ git clone https://github.com/ManageIQ/manageiq-pods
$ cd manageiq-pods
$ git checkout petrosian-1
```

Step 2: Modify the deploy parameters
```
The parameters file dictates how the application will be deployed. For a non-production use-case the memory and cpu requests and limits can be decreased. Additionally, APPLICATION_DOMAIN should be set to a hostname which will route back to your minikube VM.
```

Step 3: Run the deploy script
```
bin/deploy parameters
```


Step 4: Patch the httpd deployment
```
oc patch deployment httpd -p '{"spec":{"template":{"spec":{"containers":[{"name": "httpd", "securityContext":{"capabilities":{"add":["SYS_ADMIN"]}}}]}}}}'
```



