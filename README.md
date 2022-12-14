<h1 align="center">Lizz compatible domain name application</h1>

Lizz compatible application to add the domain name application to a lizz managed Kubernetes cluster.
The domain name application is simply a configmap resource that is added to the cluster.
This resource contains the domain name that can be used by the other applications, espacially for the ingresses.

To learn more about Lizz, see the [documentation](https://openlizz.com).

## Requirements

To add the application, you first need to have a [Kubernetes cluster initialized with Lizz](https://openlizz.com/docs/guides/init).
You also need to have the [Lizz CLI installed](https://openlizz.com/docs/installation).

## Add the application

To add the application to your cluster, run the following:

```bash
lizz add github \
    --owner=$GITHUB_USER  \
    --fleet=fleet \
    --origin-url=https://github.com/openlizz/application-domaine-name \
    --path=./ \
    --destination=domaine-name \
    --set-value value=$DOMAIN_NAME
    --personal
```

Check the [guide](https://openlizz.com/docs/guides/add) to understand how works the lizz add command.


> **Note**
> You can adapt the command depending on your use case. See the [command API](https://openlizz.com/docs/cli/lizz_add_github) for more information.

Reconcile the fleet repository to deploy the application using [Flux](https://fluxcd.io/):

```
flux reconcile source git flux-system
```

