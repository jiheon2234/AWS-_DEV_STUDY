## CloudFront?
> `CDN` (Content Delivery Network)
> 컨텐츠가 전세계 edge[^1]에 캐싱됨

- S3 bucket : 파일배포&캐싱
- Custom (HTTP)
- 캐시 개념이므로, static 컨텐츠에 유용함

## Caching
- 각 Edge에 캐시됨
- 캐쉬 안의 객체는 Cache Key[^2]에 의해 식별됨

## Cache Policy
- 언어, 장치 등의 다양한 상황에 대해서 캐시하고 싶을 경우에
HTTP Header, Cookie, QueryString 등 포함해 사용자 정의

- TTL 제어 가능, `Cache-Control` 헤더 


###Orging Request Polciy
>오리진 서버로 요청을 전송할 때 어떤 요청 헤더, 쿠키, URL 쿼리 문자열을 포함할지 정의

![](../_STATIC/CleanShot%202023-11-26%20at%2018.01.21.png)

## Invalidations
>경로를 Invalidate하여 Edge 캐시를 강제로 무효화시킬 수 있음

## Cache Behaviors
> URL 패턴에 따라, 각기 다른 동작
ex) /api/\*로 시작하면 -> 로드밸런서로, /\*로 시작하면 S3으로



[^1]:Edge Location, 전세계에 분포되어 있는 데이터 센터(216개)
[^2]:기본적으로 hostname+url


