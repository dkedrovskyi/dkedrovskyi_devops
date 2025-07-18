1. Check that the go app compiled and works locally.
2. Build docker image
   docker build -t 2424234242/dkedrovskyi/v1.0.1 .
   docker run sha256:fec793f1efd019881bd99ad025e13a4591579a82dbb4afd185dd990bd0bfada9  - check if works
   docker tag fec793f1efd0 dkedrovskyi/app:v1.0.1
   docker push dkedrovskyi/app:v1.0.1
3. Run some simple k8s, like k3s
4. kubectl create deploy demo --image 2424234242/app:v1.0.1 
   kubectl port-forward deploy/demo 8080
   check whether works
5. Update something in sources, rebuild and push new docker image  
   kubectl set image deploy demo app=2424234242/app:v1.0.2
   kubectl port-forward deploy/demo 8080
   check whether works
   
kubectl get po 
NAME                    READY   STATUS    RESTARTS   AGE
demo-6d566678c5-tfv8b   1/1     Running   0          58m
