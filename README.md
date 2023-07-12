<h1 align="center">Welcome to uyuni-slurm-monitor 👋</h1>
<p>
  <a href="https://github.com/vpenso/prometheus-slurm-exporter" target="_blank">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" />
  </a>
</p>

> 유우니를 슬럼에 연동하기 위한

## install

1. `slurm-exporter/slurm-exporter-endpoints.yaml` 파일 수정

```yaml
kind: Endpoints
apiVersion: v1
metadata:
namespace: prometheus
name: slurm-exporter
subsets:
  - addresses:
      - ip: 192.168.1.46 # <- slurm controller 아이피 입력
    ports:
      - name: slurm-exporter
        port: 8080
```

2. `slurm-gpu-metrics/slurm-gpu-metrics-endpoints.yaml` 파일 수정

```yaml
kind: Endpoints
apiVersion: v1
metadata:
  namespace: prometheus
  name: slurm-gpu-metrics
subsets:
  - addresses:
      - ip: 192.168.1.248 # <- slurm worknode 아이피 입력
      - ip: 192.168.2.34
      - ip: 192.168.2.37
      - ip: 192.168.2.38
      - ip: 192.168.2.39
    ports:
      - name: slurm-gpu-metrics
        port: 9400
```

3. `slurm-node-exporter/slurm-node-exporter-endpoints.yaml` 파일 수정

```yaml
kind: Endpoints
apiVersion: v1
metadata:
  namespace: prometheus
  name: slurm-node-exporter
subsets:
  - addresses:
      - ip: 192.168.1.46 # <- slurm worknode 아이피 입력
      - ip: 192.168.1.248
      - ip: 192.168.2.34
      - ip: 192.168.2.37
      - ip: 192.168.2.38
      - ip: 192.168.2.39
    ports:
      - name: slurm-node-exporter
        port: 9100
```

4. 해당 yaml 파일들을 `kubectl apply -f` 명령어로 적용

## Author

👤 **je.kim,moonsub**

- Github: [@je.kim,moonsub](https://github.com/je.kim,moonsub)

## Show your support

Give a ⭐️ if this project helped you!

---

_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_
