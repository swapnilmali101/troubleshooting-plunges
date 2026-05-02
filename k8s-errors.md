# k8s errors troubleshoots

___How to Debug___

If the Pod is still not running, run this command to see the exact error:

`kubectl describe pod -l app=deployment-app-name -n namespace-name`

___Common errors to look for:___

`CreateContainerConfigError` : This usually means the Secret `name-of-secret` wasn't found in the `namespace-name` namespace.

`CrashLoopBackOff` : This means the container started but died (likely because it couldn't connect to MongoDB).

___Why the "CRD" error?___

Kubernetes gives you that confusing message about "CRDs" (Custom Resource Definitions) because it assumes that if a resource isn't part of the standard library it knows about, it must be a custom one you forgot to install. In this case, it’s just a typo in the address!

| Resource Kind | Correct apiVersion |
|---|---|
| Service | v1 | 
| Pod | v1 | 
| ConfigMap / Secret | v1 | 
| Deployment | apps/v1 | 
| Ingress | networking.k8s.io/v1 |

---

## Other Resources to lookup

- [Search Kubernetes Production Issues...](https://k8s-issues.purutuladhar.com/)
