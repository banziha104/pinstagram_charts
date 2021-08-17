# [Service](https://github.com/banziha104/pinstagram_charts/blob/master/templates/pinstagram-static-ingress.yaml)

```yaml

---
apiVersion: v1
kind: Service
metadata:
  name: {{.Values.service.authService}}
  labels:
    app: {{.Values.app.authApp}}
spec:
  type : NodePort # Ingress의 Service는 NodePort 타입
  selector: # 해당 셀렉터에서 AuthApp과 관련된(auth-deploments)를 가져옮 
    app: {{.Values.app.authApp}}
    tier: {{.Values.tier.server}}
  ports:
    - port: {{.Values.port.authPort}} # 해당 포트(예:8081)로 요청이들어오면
      targetPort: {{.Values.port.authPort}} # 현재 셀렉터를 통해 지정된 개체들의 타겟포트로 요청 전달 
      protocol: TCP

---
apiVersion: v1
kind: Service
metadata:
  name: {{.Values.service.contentsService}}
  labels:
    app: {{.Values.app.contentsApp}}
spec:
  type : NodePort
  selector:
    app: {{.Values.app.contentsApp}}
    tier: {{.Values.tier.server}}
  ports:
    - port: {{.Values.port.contentsPort}}
      targetPort: {{.Values.port.contentsPort}}
      protocol: TCP
---
apiVersion: v1
kind: Service
metadata:
  name: {{.Values.service.geoService}}
  labels:
    app: {{.Values.app.geoApp}}
spec:
  type : NodePort
  selector:
    app: {{.Values.app.geoApp}}
    tier: {{.Values.tier.server}}
  ports:
    - port: {{.Values.port.geoPort}}
      targetPort: {{.Values.port.geoPort}}
      protocol: TCP
---
apiVersion: v1
kind: Service
metadata:
  name: {{.Values.service.talkService}}
  labels:
    app: {{.Values.app.talkApp}}
spec:
  type : NodePort
  selector:
    app: {{.Values.app.talkApp}}
    tier: {{.Values.tier.server}}
  ports:
    - port: {{.Values.port.talkPort}}
      targetPort: {{.Values.port.talkPort}}
      protocol: TCP
```