# LEGarcia





```bash
ssh lab-user@studentvm.x64sh.example.opentlc.com
```

```bash
oc delete project $GUID-deployments
```

```bash
oc new-project $GUID-deployments --display-name="OpenShift Deployments"
```

```bash
vim ocp-probe-deployment.yaml
```

```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ocp-probe
spec:
  selector:
    matchLabels:
      app: ocp-probe
  replicas: 1
  template:
    metadata:
      labels:
        app: ocp-probe
    spec:
      containers:
      - name: ocp-probe
        image: quay.io/gpte-devops-automation/ocp-probe:v0.3
        ports:
        - containerPort: 8080

```

```bash
oc create -f ocp-probe-deployment.yaml
```

```bash
oc rollout status deployment ocp-probe
```

```bash
oc scale deployment ocp-probe --replicas=3
```

```bash
oc rollout status deployment ocp-probe
```

```bash
oc get all
```

```bash
oc describe rs ocp-probe-
```

```bash
oc edit deployment ocp-probe
```

```bash
oc rollout status deployment ocp-probe
```

```bash
oc get all
```

```bash
oc describe deployment ocp-probe
```

```bash
oc delete project $GUID-deployments
```
