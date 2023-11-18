## Route53이란?
> AWS에의해 관리되는 DNS => 내가 DNS기록을 업데이트 가능

*53은 DNS에서 사용하는 포트번호를 딴거임*

## Record Types
 - `A` :  hostname을 IPv4에 매핑
 - `AAAA` : hostname을 IPv6에 매핑
 - `CNAME` : hostname을 hostname에 매핑
	 - 최상위도메인에는 못만듬
- `NS` : Name Servers[^1] for the Hosted Zone

## Hosted Zone
> 트래픽을 도메인, 서브도메인으로 라우팅하기위한 기록 보관소

- Public Hosted Zones : 전세계 어디서나 접근 가능한 도메인/서브도메인 관리
- Private Hosted Zones : VPC에서만 접근 가능 한 도메인/서브도메인 관리


## CNAME vs Alias
- `CNAME` : hostname을 hostname에 매핑
- `Alias`: hostname을 AWS Resource에 매핑 
	- 최상위도메인 가능, 자동으로 IP주소 변화 감지


## Routing Policies
- simple :  단일 리소스에 대한 라우팅 쿼리 (여러 주소가있다면, 여러개를 줌 =>랜덤으로 클라이언트가선택)
- Weighted : 여러 리소스에 가중치를 부여 => Route53이 가중치에 따라 트래픽을 분산 (여러개중 하나 줌)
- Latency : 가장 대기시간이 적은 곳으로 redirect
- Geolocation : 위치기반
- DemoGeoPolicy : 위치기반 + bias(편향)
- Ip based






[^1]: 도메인 이름을 해당하는 IP 주소로 변환하는 역할