# 프론트엔드 배포 파이프라인
## 개요
![Screenshot 2025-05-29 at 11 38 46 PM](https://github.com/user-attachments/assets/54e8e9a4-21b8-4af6-b617-18e08f26c762)

## 주요 링크
- S3 버킷 웹사이트 엔드포인트: http://practice-performance-optimization.s3-website-us-east-1.amazonaws.com/
- CloudFront 배포 도메인 이름: https://d2hooo0a4mvwdi.cloudfront.net

## 주요 개념
- GitHub Actions과 CI/CD 도구
  - GitHub Actions: 빌드와 배포, test를 자동화할 수 있는 플랫폼
  - CI/CD: 지속적 통합(CI, Continous Integration) 및 지속적 제공/배포(CD, Continous Delivery, Deployment)
    - 지속적 통합이란 코드 변경사항을 레포지토리에 자동으로 통합해주는 기능이며, 지속적 제공/배포로는 레포지토리에 통합된 코드를 자동으로 프로덕션 환경에 배포해주는 기능이다.
    - CI/CD 도구 예시 : GitHub Actions, Jenkins, GitLab CI/CD
- S3와 스토리지
  - S3: Amamzon Simple Storage Service
    - 어디에서나 데이터를 저장하고 검색할 수 있도록 클라우드 환경에서 구축된 객체 스토리지 서비스이다.
  - 스토리지: 데이터를 저장하는 매체
- CloudFront와 CDN
  - CloudFront: 사용자에게 웹 콘텐츠를 더욱 빨리 배포하도록 지원하는 웹 서비스
    - 엣지 로케이션이라는 데이터 센터의 전 세계 네트워크에 일정기간 데이터를 저장한다. 
    - 사용자가 콘텐츠를 요청하면 지연 시간이 가장 낮은 엣지 로케이션으로 요청을 라우팅하여 최적의 성능으로 콘텐츠를 제공한다.
  - CDN: 콘텐츠 전송 네트워크(Content Delivery Network 또는 Content Distribution Network)
    - 콘텐츠를 효율적으로 전달하기 위해 여러 노드를 가진 네트워크에 데이터를 제공 
- 캐시 무효화(Cache Invalidation): 캐시된 콘텐츠를 무효로 선언하는 프로세스
  - 객체가 캐시된 후 일반적으로 객체가 만료되거나 스토리지 공간 확보를 위해 삭제가 이루어지기 전까지 캐시된 데이터는 유지된다. 
- Repository secret과 환경변수
  - Repository secret: token 값과 같이 사용자에게 공개되어서는 안되는 민감한 정보를 저장한다.
  - 환경변수: 일반적인 구성 값을 저장하고 워크플로우의 각 단계에서 사용할 수 있는 값

## CDN과 성능최적화
|CDN 적용 전|CDN 적용 후|
|:---:|:---:|
|<img src="https://github.com/user-attachments/assets/63386a0b-9188-4b54-8edf-5a2d6354fd62" width="400">|<img src="https://github.com/user-attachments/assets/c43516a4-f78d-4cb0-867e-91ae56d6dc27" width="400">|
|총 로딩 시간: 2.24s|총 로딩 시간: 180ms|

CDN 적용 후, 데이터 로드 시간이 1/10 가량으로 감소했다. 

### References
- [Amazon S3란 무엇인가요?⏤AWS 홈페이지](https://docs.aws.amazon.com/ko_kr/AmazonS3/latest/userguide/Welcome.html)
- [Amazon CloudFront란 무엇입니까?⏤AWS 홈페이지](https://docs.aws.amazon.com/ko_kr/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)
- [CloudFront 개념 원리 & 사용 세팅 💯 정리⏤Inpa Dev 블로그](https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-CloudFront-%EA%B0%9C%EB%85%90-%EC%9B%90%EB%A6%AC-%EC%82%AC%EC%9A%A9-%EC%84%B8%ED%8C%85-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC)
- [캐시 무효화 개요⏤Google Cloud 문서](https://cloud.google.com/cdn/docs/cache-invalidation-overview?hl=ko)
