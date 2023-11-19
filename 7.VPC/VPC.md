#AWS 
*Virtual Private Cloud는 AWS Developer 시험에서는 그렇게 깊게 들어가지 않음*

## VPC?
- 클라우드 내의 가상 네트워크를 private하게 설정하고 관리 
- VPC안에 여러 Subnet이 있는 구조
- Route table을 이용해 인터넷이나 다른 서브넷간의 접근을 설정
![](../_STATIC/CleanShot%202023-11-19%20at%2010.20.29.png)


## Internet GateWay & NAT Gateway
- Internet Gateways : VPC 인스턴스가 인터넷과 연결되게 함
- NAT Gateways : Private Subnet에 있는 인스턴스가, private한 상태로 인터넷에 접근가능하도록 함

## NACL & Security Groups
- NACL : 서브넷 트래픽에 관한 방화벽 (IP주소에 기반한 ALLOW/DENY)
- Security Groups : EC2인스턴스에 관한 방화벽(Only Allow, IP 또는 다른 Security 참조 가능)

## VPC Flow Logs
- 내 인터페이스로 들어가는 모든 IP 트래픽 정보 캡쳐 (VPC, SUBNET, ENI)
- 네트워크 문제가 생길때 봐야됨

## VPC Endpoints
- AWS 서비스에 private한 네트워크로 연결하도록 허용
- VPC 안에서만 사용 가능



## 시험요약
- `VPC` : Virtual Private Cloud
- `Subnets` : 특정 AZ에 연결됨, VPC의 네트워크 파티션
- `Internet Gateway` : VPC 레벨에서, 인터넷(WWW) 접속해줌
- `Nat Gateway` : private subnet에 인터넷 Access
- `NACL` : Stateless, in/outbound 서브넷 규칙
- `Security Groups` :  EC2 인스턴스 레벨에서 작동
- `VPC Peering` :  VPC2개가 IP범위가 겹치지 않으면 (전이 X)
- `VPC Endpoints` : AWS 서비스에 private access 제공
- `VPC Flow Logs` : 네트워크 트래픽 로그
- `Site to Site VPN` : on-premise[^1]와 AWS VPC사이에 VPN을 통해서 연결하는 방법
- `Direct Connect` : AWS에 대한 직접 연결 (개비싸고 오래걸림)




[^1]: 사무실이라고 생각하자