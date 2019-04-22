# openshift-dockerhub-wordpress

Deploy dockerhub wordpress image in OpenShift with minimal changes using a
self-contained template.

This template is based in the template used in [this blog post](https://blog.openshift.com/running-wordpress-easy-way/) located in
[this repository](https://github.com/openshift-evangelists/wordpress-quickstart)
and translated to yaml.

You will need to create a wordpress imagestream in openshift project uploading
image or importing it. Choose one of the following:

* Import image:
```
oc import image docker.io/wordpress --confirm --namespace=openshift
```

* Upload wordpress image to registry in openshift project following this
  procedure:
```
docker login docker-registry-default.youropenshift.example.com -p $(oc whoami -t)
docker pull wordpress
docker tag wordpress docker-registry-default.youropenshift.example.com/openshift/wordpress
docker push docker-registry-default.youropenshift.example.com/openshift/wordpress
```

Install template:
```
oc create -f classic-standalone.yaml
```
