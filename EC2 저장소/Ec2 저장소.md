#AWS 

## EBS Volume이란?
> `Elastic Block Store` : 인스턴스 실행중 접근하는 *네트워크* 드라이브
- 인스턴스가 종료되더라도, 데이터가 여기에 살아있음 => 새 인스턴스에서 사용가능
- 인스턴스:EBS = 1:N
- 네트워크를 사용하기 때문에 약간 지연
- 용량을 미리 정해야 됨
- AZ[^1] 에 따라 분리됨

## EBS Snapshots
- EBS Volume의 백업
- AZ나 Region으로 복사 가능
### 스냅샷 기능
 - Snapshot Archive : `archive tier`로 옮기고, 24~72시간 후에 복구 가능 (쌈)
 - Recycle Bean : 생략
 - Fast Snapshot Restore (FSR) : 지연이 없도록 하는 옵션 (비쌈)

## AMI란?
>`Amazon Machine Image`
-  EC2 인스턴스를 시작하는 데 필요한 모든 정보를 포함하는 템플릿(패키지)
- 빠른 베포, 일관된 환경
- Region별로 사용

## EC2 Instance Store
- 성능을 위해, 가상 디스크가 아닌 실제 하드웨어 디스크 연결
- I/O 성능 개빠름
- 인스턴스가 종료되면 저장된 데이터가 소실됨 => *지속적인 데이터 저장이 필요없는 캐시, 버퍼에 유리*

## EBS Volume Types
- gp2/gp3 : 범용 SSD  *boot volume 가능*
- io1/io2 : 고성능 SSD *boot volume 가능*
- st1 : 저가형 HDD
- sc1 : 초저가형 HDD


### General Purpose (gp2/gp3)
- 지연시간낮음, 비용효율
- boot volume, 가상 데스크탑, 개발/테스트

### Provisioned Iops (io1/io2)
- io 작업많이필요할때
- **DB**에 주로 쓰임
- *io2*만 쓰면 된다고 함


## EBS Multi-Attach (io1/io2만 사용 가능)
[EBS Volume이란?](#EBS%20Volume이란?) 에서, 인스턴스와 EBS는 1:N이라고 했지만, 
`io1`,`io2` EBS에 Multi-Attach 기능을 사용하면, 한번에 최대 **16개** EC2에 연결 가능
- 같은 *AZ*에서만 가능
- cluster-aware[^2] 파일 시스템만 가능 

## EFS
> `Elastic File System` : 네트워크 파일 시스템

- 여러 AZ의 여러 Ec2에 마운트 가능
- 가용성 높고, 확장성 및 간편함이 필요할 때 사용, <span style="color:red">~~비쌈~~</span>


## EBS VS EFS
- EBS
	- 하나의 인스턴스에 첨부됨
	- AZ레벨로 잠김 (다른데로 옮기려면 snapshot)
- EFS 
	- AZ에구애받지 않음
	-  비싸지만, EFS-IA로 비용 절감 가능









[^1]:Amazon Availability Zone (Region > AZ)
[^2]:여러 노드가 동일한 데이터 접근 가능한 파일 시스템 (일반적❌)