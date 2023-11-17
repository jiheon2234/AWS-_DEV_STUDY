#AWS 

## ~~CLB(Classic Load Balancer) 는 더이상 사용하지 않음~~

## ALB(Application Load Balancer)
- HTTP(S) 트래픽 처리  (웹소켓도 지원)
- 다중 앱에 부하 분산 (같은 컨테이너도 가능)
- 경로, 도메인, 쿼리스트링, 헤더 등으로 라우팅 가능
- 동적 포트 매핑
- EC2, task, Lambda, IP 등의 target group[^1]

**알아두면 좋을 것들**
- application server는, client의 ip를 직접적으로 보지 않음
	- 대신 `X-Forwarded-For`라는 헤더에 삽입됨
	 - `X-Forwarded-Port`,`X-Forwarded-Proto` 를 통해 포트, 프로토콜을 얻음


## NLB (Network Load Balancer)
  - 4계층 (TCP&UPD)
  - AZ당 1개의 고정 IP
  - ALB 앞에서 동작 가능
  - TCP, HTTP, HTTPS로 Health Checks
  - ~~`free tier`에 포함되지 않음~~


  ## Gateway Load Balancer
  - 3계층 (Network Layer)에서 작동
  - IP packet기반으로 트래픽 관리
  - 방화벽, 침입탐지 시스템 등에 네트워크 트래픽을 분산하는 역활
  - 2가지 역활
	  - Transparent Network Gateway : 모든 트래픽에 대한 하나의 입구/출구
	  - Load Balancer : 트래픽 분산
   - `GENEVE`프로토콜 (6081포트)


   ## Sticky Sessions(Session 선호도)
   > 로드밸런싱을 통해 인스턴스로 redirect될때, 항상 같은 instance로 가는 기능
   - ALB, NLB에서 가능
   - 쿠키🍪 사용
   - 이걸 허용하면, 밸런스 문제가 생길수도

   ### Cookie Names
**Application-based Cookies**
   - 기본 쿠키
   - Application Cookie
	   - load balancer가 만듬
	   - 이름 : `AWSALBAPP`

**Duration-based Cookies[^2]**
- load balancer가 만듬
- 이름: `AWSALB`

## Cross-Zone load Balancing
> 여러 AZ에 걸쳐 로드 밸런싱을 하는것
- Application Load Balancer
	- 기본 옵션임 , 비용부과❌
- Network, Gateway Load Balancer
	- 기본옵션아님, 비용부과됨


## SSL/TLS
![](../_STATIC/CleanShot%202023-11-17%20at%2021.31.00.png)
Server Name Indication (SNI)"
![](../_STATIC/CleanShot%202023-11-17%20at%2021.37.55.png)

## Deregistration Delay
> 인스턴스가 해제될때(또는 unhealthy), 적용되는 지연 시간
- 새 요청은 받지 않지만, 이미 받은 요청은 완료 후 해제됨

## Auto Scaling Group
> EC2인스턴스의 집합을 자동으로 확장 및 축소 (cloudwatch 알람을 통해)
- `Scale out` :  add,  `Scale in`  : remove
- 언제라도, 최대의/최소의 인스턴스가 실행 가능
- 로드 밸런서에 링크됨
- health check를 통해서, 적합하지 않다면 제거 가능
- ~~무료라곤 하지만, EC2에 대해선 비용부과됨~~

### Dynamic Scaling Policies
- Target Tracing Scaling : ex)CPU 평균 사용량이 40%에서 머물도록
- Simple/Step Scaling : CloudWatch 알림이 발동하면, 조정하기
- Scheduled Action : 특정 시간의 트래픽이 예상될경우
- Predictive Scaling : 머신러닝으로 예측

CPU 사용량, RequestCount 등의 지표 사용

### Instance Refresh
> launch template을 업데이트하고, 모든 EC2 새로 생성





[^1]:트래픽을 전달할 대상
[^2]:지속시간 기반
