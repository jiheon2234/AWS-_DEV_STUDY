#AWS 


## EC2란?
> `Elastic Compute Cloud`  :   탄력적 컴퓨터 클라우드

### 구성 옵션
- Linux, Windows, Mac  OS 사용 가능
- CPU 사양, RAM사양, 저장공간
- 네트워크 유형
- 방화벽 규칙
- Bootstrap script


## User data
-  bootstrap[^1]  을 통해 소프트웨어 설치,  파일 다운 등을 자동화 가능



## Instance Types
><span style="color:a9b5ff">m</span> <span style="color:yellow">5.</span><span style="color:green">2Xlarge</span> 라는 인스턴스가 있다면
- `m` : 인스턴스 클래스
- `5` : 세대
- `2Xlarge` : 클래스의 크기

## Security Groups
> - AWS 보안
>- 인스턴스 트래픽에 대한 제어(허용)
>- `allow rules`

**인스턴스의 방화벽**
포트, IP범위, inbound[^2],outbound[^3]
*0.0.0.0*은 모두허용임

- 인스턴스와 다대다관계임
- 지역과 VPC로 묶여있음 
- 인스턴스 밖에서 동작
- SSH 접근을 위한 분리된 보안그룹 권장
- 기본적으로, 모든 inbound는 막혀있고, outbound는 뚤려있음
*모든 timeout은 보안그룹때문임*





## ssh연결
```bash
ssh -i 인증키.pem ec2-user@[public IP]  
#ec2-user는 AmazonLinux인스턴스 생성시 존재
```

## Purchasing option
- On demand : 필요에 따라 서비스 사용, 이에 따라 요금 지불
- Reserved : 사용할 기간을 정하고, 할인많이 (ec2에만)
- Saving Plans : 넓은 범위에서(ec2,lambda) 사용량 미리 약정
- Spot instances : 많이 할인되지만, 예고없이 중단될 수 있음
- Dedicated Host: 물리적인 Ec2 서버 단독사용
- Capacity Reservations :  특정 인스턴스 유형을 특정 지역에서 미리 예약하고, 필요할 때 사용할 수 있도록

[^1]: 이 컴퓨터 시스템이 스스로 시작하고 실행되는 프로세스 (부팅, 시작할때 단 한번)
[^2]: 밖에서 안으로
[^3]:안에서 밖으로