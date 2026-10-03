# Helm chart: sales-service

This chart deploys `sales-service` independently.

## Expected image

```text
<AWS_ACCOUNT_ID>.dkr.ecr.<REGION>.amazonaws.com/sales-service:<GIT_SHA>
```

## Local validation

```bash
helm lint ./helm
helm template sales-service ./helm \
  --set image.repository=example/sales-service \
  --set image.tag=dev
```

## Notes

- RollingUpdate: `maxUnavailable=0`, `maxSurge=1`.
- Readiness/liveness probes are enabled by default.
- HPA is disabled by default.
- Adjust `values.yaml` if the application uses another port or health endpoint.
