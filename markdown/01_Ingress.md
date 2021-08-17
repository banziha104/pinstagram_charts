# [Ingress](https://github.com/banziha104/pinstagram_charts/blob/master/templates/pinstagram-static-ingress.yaml)

```yaml
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: {{.Values.app.pinstagramNetworkApp}}
  annotations:
    {{ if eq .Values.level "prod"}} # Helm을 이용해 현재 상태가 prod이면 구글의 ingress를 사용
    kubernetes.io/ingresss.global-static-ip-name: pinstagram-static-ip
    networking.gke.io/managed-certificates: {{.Values.ssl.appName}}
    kubernetes.io/ingress.class: "gce"
    {{else}} # 아닌경우 nginx의 ingres를 사용
    nginx.ingress.kubernetes.io/rewrite-target: /
    {{end}}
  labels:
    app: {{.Values.app.pinstagramApp}}
spec:
  rules:
    - http:
        paths:
          - path: {{.Values.path.authPath}} # 해당되는 path로 오면 
            pathType: ImplementationSpecific 
            backend:
              serviceName: {{.Values.service.authService}} # 해당되는 서비스의
              servicePort: {{.Values.port.authPort}} #해당되는 포트로 전달 
          - path: {{.Values.path.contentsPath}}
            pathType: ImplementationSpecific
            backend:
              serviceName: {{.Values.service.contentsService}}
              servicePort: {{.Values.port.contentsPort}}
          - path: {{.Values.path.geoPath}}
            pathType: ImplementationSpecific
            backend:
              serviceName: {{.Values.service.geoService}}
              servicePort: {{.Values.port.geoPort}}
          - path: {{.Values.path.talkPath}}
            pathType: ImplementationSpecific
            backend:
              serviceName: {{.Values.service.talkService}}
              servicePort: {{.Values.port.talkPort}}
```