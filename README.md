# Better error pages

This deployment is based on: [tiringpi-errors](https://gitlab.com/vstrycek/turingpi-error-pages) which is in turn based on [error-pages container](https://github.com/tarampampam/error-pages)

## What it does
It uses priority in Traefik to display a nice error page in case it's not handled by the targeted app. It can also be added into any service ingress if that service does not handle 404, 500, etc. errors in a nice way.

## Themes

You can use pre-built themes by changing the `TEMPLATE_NAME` variable in  `error-pages-deployment.yaml` 

```yaml
.
.
.
        env:
        - name: TEMPLATE_NAME
          value: "app-down"
        - name: SHOW_DETAILS
          value: "true"
        ports:
.
.
.
```

Theme demonstrations: [HERE](https://tarampampam.github.io/error-pages/)

## Prometheus

Container exposes /metrics in prometheus format

## Limits

- Limited to 16MB RAM - Max 32MB
- CPU: 50m
- Image size: 4.66MB
- readOnlyRootFilesystem: true
- runAsNonRoot: true
- allowPrivilegeEscalation: false
