# Client 배포 자동화

## Git Repository Fork

## 파이프라인 생성

- AWS 콘솔 -> CodePipeline
- 파이프라인 생성
- 파이프라인 이름 : IAM USER-000-pipeline, 다음

## 소스 스테이지

- 소스 공급자 : Github 버전2
- Github에 연결 버튼
- 연결이름 지정 : IAM USER-000-github
- 새 앱 설치 버튼
- gitHub 로그인
- Only select repositories
- Select repositores에서 deploy-automation 선택
- Save 버튼
- 연결 버튼
- 레포지토리 이름 지정 your_github_ideploy-automation
- 파이프라인 트리거 지정
  - 브랜치 내 푸쉬
- 브랜치 이름 지정
  - main
- 다음 버튼

## 빌드 스테이지

- 빌드 공급자 : AWS CodeBuild
- 프로젝트 생성 버튼
- 프로젝트 이름 : IAM USER-000-build
  - 구성 설정
    - 운영체제 : Ubuntu
    - 런타임 : Standard
    - 이미지 : aws/codebuild/standard:7.0
  - CodePipeline으로 계속 버튼
  - 사이트에서 나가기 나올 경우 "나가기" 선택
- 환경변수 추가
  - 이름 : REACT_APP_API_URL
  - 값 : Lambda URL (맨 뒤 `/` 삭제할 것)
- 다음 버튼

## 배포 스테이지

- 배포 공금자 : Amazon S3
- 리전 : 아시아 태평양 (서울)
- 버킷 : IAM USER-000-client(생성했던 s3 버킷)
- 배포하기 전에 파일 압축 풀기 체크
- 다음 버튼

## 검토 후 파이프라인 생성

- 환경변수에서 url 뒤 `/` 없는거 확인
- 파이프라인 생성 버튼
