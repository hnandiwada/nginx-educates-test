# NGINX Sample App for Tanzu Desktop
Using [Paketo Buildpacks
docs](https://paketo.io/docs/buildpacks/language-family-buildpacks/nginx/)
Repo taken from [Paketo Buildpacks
Samples](https://github.com/paketo-buildpacks/samples)

## Build the image
```
cd nginx-sample
pack build hnandiwada/nginx --buildpack gcr.io/paketo-buildpacks/nginx   --builder paketobuildpacks/builder:base
docker push hnandiwada/nginx
```

## Running on vanilla k8s
In nginx-sample:
```
kubectl apply -f deployment.yaml
kubectl port-forward pod/nginx 8080
curl localhost:8080
```
You should see "Powered by Tanzu Desktop"

## Using Tilt
In nginx-sample:
```
tilt up
```
Make sure the pod is not already up beforehand and that you're not already
port-forwarding in a separate terminal.


