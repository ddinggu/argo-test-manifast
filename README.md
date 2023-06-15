# Helm 마이그레이션

기본 쿠버네티스 리소스 구성 방법에서 Helm으로 마이그레이션

- 기존 방법의 문제점 파악
- 어플리케이션 배포 자동화를 위한 GitOps 환경 구축

## Helm

쿠버네티스 리소스 관리를 돕기 위한 패키지 매니저

### 기존 리소스 관리의 어려움

1. 로컬 코드 상태와 라이브 리소스 상태의 불일치
2. 어플리케이션 수명주기 관리의 어려움
3. 추상화된 리소스들의 복잡성
4. 정적인 선언형 리소스
5. 대규모 리소스 관리의 어려움(ex. 마이크로서비스)

### Helm을 통한 문제점 해결

1. 리소스 복잡성의 추상화
2. 릴리즈 이력 관리
3. 동적으로 구성된 선언형 리소스, 지능형 배포
4. 로컬 - 라이브 상태의 일관성 유지
5. 라이프사이클 간 Hook 정의 가능
6. 템플릿 기반 동적변수 설정을 통한 다양한 운영환경 관리 편의성

### Helm 프로젝트 파일 구조

`helm create <프로젝트 명>` 으로 생성

```
./helm-chart
├── Chart.yaml # 차트 메타데이터(기본 정보)
├── charts # Chart 의존성 관리(다른 Chart를 체이닝 할 수 있음)
├── templates # 쿠버네티스 리소스를 정의하는 템플릿
│   ├── NOTES.txt
│   ├── _helpers.tpl
│   ├── deployment.yaml
│   ├── hpa.yaml
│   ├── ingress.yaml
│   ├── service.yaml
│   ├── serviceaccount.yaml
│   └── tests
│       └── test-connection.yaml
└── values.yaml # 기본 차트 변수를 정의하여 템플릿에 주입
```
