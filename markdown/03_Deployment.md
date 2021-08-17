# [Deployment](https://github.com/banziha104/pinstagram_charts/blob/master/templates/pinstagram-auth-deployment.yaml)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name:  {{.Values.deploy.auth}}
  labels:
    app: {{.Values.app.authApp}}
spec:
  selector:
    matchLabels:
      app: {{.Values.app.authApp}}
      tier: {{.Values.tier.server}}
  template:
    metadata:
      labels:
        app: {{.Values.app.authApp}}
        tier: {{.Values.tier.server}}
    spec:
      containers:
        - name: {{.Values.app.authApp}}
          image: {{.Values.images.auth}} # GCR에 저장된 이미지를 불러옮
          ports:
            - containerPort: {{.Values.port.authPort}}
              hostPort:  {{.Values.port.authPort}}
          readinessProbe:  # GKE는 readinessProbe를 이용해 서비스가 가능한 상태인지 아닌지를 확인함, 명시하지 않을 경우 "/"로 헬스체크
            periodSeconds: 60
            httpGet:
              port: {{.Values.port.authPort}}
              path: {{.Values.path.healthCheck.authPath}}
              scheme: HTTP
```