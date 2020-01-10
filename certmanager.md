2. Create a namespace `cert-manager`.
```
kubectl create namespace cert-manager
```

3. Install Cert-manager
Now, Install the cert manager and CRDS. it will install issuer and clusterissuer also.

```
kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v0.12.0/cert-manager.yaml
```

You should get below output.

```
clusterrole.rbac.authorization.k8s.io/cert-manager-view configured
Warning: kubectl apply should be used on resource created by either kubectl create --save-config or kubectl apply
clusterrole.rbac.authorization.k8s.io/cert-manager-edit configured
service/cert-manager created
service/cert-manager-webhook created
deployment.apps/cert-manager-cainjector created
deployment.apps/cert-manager created
deployment.apps/cert-manager-webhook created
mutatingwebhookconfiguration.admissionregistration.k8s.io/cert-manager-webhook created
Warning: kubectl apply should be used on resource created by either kubectl create --save-config or kubectl apply
validatingwebhookconfiguration.admissionregistration.k8s.io/cert-manager-webhook configured

```

Verify the installation by below command.
```
kubectl get pods --namespace cert-manager
```
```
NAME                                       READY   STATUS    RESTARTS   AGE
cert-manager-cainjector-58f48c4cb9-2q8wp   1/1     Running   0          1m
cert-manager-cb5f48858-zpzh2               1/1     Running   0          1m
cert-manager-webhook-74d98fdc7b-nbv8x      1/1     Running   0          1m
```


5. Create Let'sencrypt issuer 
Now let's create issuer file to issue TLS certificates to the domains. You can create staging issuer to test, But we will directly create production issuer.
```
apiVersion: cert-manager.io/v1alpha2
kind: ClusterIssuer
metadata:
  name: letsencrypt-prod
  namespace: cert-manager
spec:
  acme:
    # The ACME server URL
    server: https://acme-v02.api.letsencrypt.org/directory
    # Email address used for ACME registration
    email: vishal@vishalvyas.com
    # Name of a secret used to store the ACME account private key
    privateKeySecretRef:
      name: letsencrypt-prod
    # Enable the HTTP-01 challenge provider
    solvers:
    - http01:
        ingress:
          class: nginx

```

```
cert-manager.io/cluster-issuer: "letsencrypt-prod"
```

