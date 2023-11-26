#AWS 

## RDS - Storage Auto Scaling
> AWS 감지 기능으로 자동으로 DB저장공간을 늘림


## Read Replicas
- 최대 15개 복제
- Within AZ, Cross AZ, Cross Region
- *비동기적으로* 이루어져서, 결과적으로 최종 일관성을 가짐
- 복제픔은 승급될수도 있음
- 복제품은 SELECT만 가능

## Multi AZ  (재난복구용)
- *동기적 복구* (대기용)
- 1 DNS (문제가 생기면 자동 장애 복구)
- 그냥 복구 대기용 (읽기❌/쓰기❌ )
- `Read Replicas`도 설정 가능

**Single-AZ에서  Multi-AZ로 바꾸기 위해선, DB를 멈출 필요가 없음**



## Amazon Aurora
> AWS의 독점 DB (Mysql, Postgres 호환)
- 3AZ에 걸쳐, 6개의 복사본을 만들어줌
- 자동복구, 장애조치

Auora DB Cluster
![](../_STATIC/CleanShot%202023-11-18%20at%2013.33.40.png)




## ElasticCache
> 관리형 in-memory 캐시 서비스 (redis 지원)


### Lazy Loading/Cache-Aside/Lazy Population
캐시에 데이터가 있으면 가져오고 끝, 없으면 DB에서 가져오고 캐시에 씀
- 단점 : 읽을때 캐시가 없으면 3번 왔다갔다함

### Write Through
DB가 업데이트될때마다, 캐시 업데이트(추가)
- 단점 : Write할때마다 캐시에도 써야됨

### TTL
Time to Live



 