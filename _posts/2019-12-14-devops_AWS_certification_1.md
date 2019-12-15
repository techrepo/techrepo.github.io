---
title: "AWS_cert_핵심서비스_1"
header:
 overlay_image: /assets/images/overlayimage.jpg
categories:
  - DevOps
tags:
  - AWS
use_math: true
toc: true
toc_label: "페이지 주요 목차"
toc_sticky: true
---
AWS 핵심 서비스

## AWS 글로벌 인프라 (AWS 호스팅)

### 리전
- 2개 이상의 가용 영역을 호스팅하는 지리 영역
- 리전은 서로 완전히 독립된 엔터티
- 한 리전의 리소스는 다른 지전으로 자도 복제되지 않음

### 가용 영역 (AZ)
- 특정 리전 내에 존재하는 데이터 센터들의 모음
- 각 가용 영역들은 서로 격리되어 있지만 지연 시간이 짧은 링크로 연결
- 물리적으로 구분된 독립적 인프라
- 물리적, 논리적 분리
- 별도의 무정전 전원 공급 장치(UPS), 현장 예비 발전기, 냉각 장비, 네트워킹 및 연결 수단
- 독립적인 전력 획사의 서로 다른 전력망을 통해 전력 공급
- 다중 AZ에 결쳐 프로비저닝 할 것을 권장

### 엣지 로케이션
- CloudFront라고 하는 CDN호스팅
- 여러 엣지 로케이션과 리전으로 구성된 글로벌 네트워크를 활용하면 보다 빠른 컨텐츠 전송 가능
- 리전 및 가용 영역과 비슷하게 인구 밀도가 높은 지역에 위치

----

## VPC

### 기본 정보
* AWS의 네트워킹 서비스
* 온프레미스 네트워크와 동일한 여러 가지 개념 및 구성을 사용하는 클라우드 내 프라이빗 네트워크 생성 가능
* 제어, 보안 및 유용성을 저해하지 않고도 네크워크 설정의 복잡성이 상당 부분 추상화되어 있음
* IP 주소 공간, 서브넷, 라우팅 테이블과 같은 일반 네트워킹 구성 항목 정의 가능
* EC2, RDS 등 여러 서비스와 통합

### 기능
* 리전 및 가용 영역의 AWS 글로벌 인프라를 기반으로 함
* 리전 내에 있으며 여러 가용 영역에 걸쳐 확장 가능
* 다중 VPC 생성 가능
* 여러 서비넷에 의해 분할되는 하나의 IP 주소 공간 정의 가능
* 서브넷과 인터넷 사이의 트래픽을 제어하기 위해 서브넷에 대한 라우팅 테이블 구성 가능
* VPC 내 모든 서브넷은 서로 통신 가능

----

## AWS Direct Connect

### 기본 정의
* 온프레미스에서 AWS로의 전용 네트워크 연결

----

## 보안 그룹

### 기본 정보
* 내장 방화벽과 같은 개념으로 인스턴스에 대한 접근성을 완벽하게 제어
* 보안 그룹 규칙을 구성하여 어떤 트래픽을 허용/거부 할 것인지 제어
* 해당 인스턴스를 100% 프라이빗 또는 퍼블릭 상태로 유지하거나 혹은 그 중간 수준의 상태로 유지하는 등 다양한 구성 가능
* 인바운드, 아웃바운드, 트래픽 유형, 프로토콜, 포트 범위 및 소스 별 구성 가능
* 사용 중인 인스턴스에 필요한 트래픽이 무엇인지 파악하고 그 트래픽만 특별히 허용할 것을 권장

----

## Amazon Lightsail

### 기본 정보
* 가상 프라이빗 서버를 시작하고 관리할 때 사용할 수 있는 가장 간편한 방법으로 설계
* 프로젝트 착수에 필요한 모든 것이 포함되어 있음
   * 가상버신
   * SSD
   * 데이터 전송
   * DNS 관리
   * 고정 IP 주소

----

## AWS Batch

### 기본 정보
* 수 많은 배치 컴퓨팅 작업을 효율적으로 실행 가능
* 제출된 배치 직업의 볼륨 및 특정 리소스 요구 사향에 따라 최적의 수량 및 유형의 컴퓨팅 리소스를 동적으로 프로비저닝

----

## AWS Lambda

### 기본 정보
* 서버를 프로비저닝하거나 관리할 필요 없이 코드를 실행할 수 있는 컴퓨팅 서비스
* 필요한 때에만 코드 실행
* 초당 수천 건의 요청으로 자동 실행
* 코드가 실행되지 않는 시간에 대해서는 비용 발생하지 않음
* 모든 래플리케이션, 백엔드 서비스에 대한 코드 실행 가능
* 고가용성 컴퓨팅 인프라에서 코드 실행
* 서버 및 운영체제 유지 관리, 용량 프로비저닝, Auto Scaling, 코드 모니터링, 로깅 등 모든 관리 기능 제공
* 다양한 프로그래밍 언어 지원
* AWS CodePipline, AWS CodeDeploy를 통해 자동 배포 가능
* 마이크로 서비스 아키텍처 구축

### 옵션
* 최대 512MB 디스크 공간
* 메모리 128MB ~ 3,008MB
* 최대 15분까지만 실행
* 최대 6MB의 요청 및 응답
* 최대 128KB의 이벤트 요청 본문

### 사용 예
* 백업 자동화
* S3에 업로드된 객체의 처리
* 이벤트 중심의 로그 분석
* 이벤트 중심의 변환
* IoT
* 서버리스 웹사이트 운영
* Amazon Kinesis를 통한 실시간 스트리밍 데이터 처리
  * 애플리케이션 활동 추적
  * 트랜잭션 주문 처리
  * 클릭스트림 분석
  * 데이터 정리 측정치
  * 생성 로그 필터링
  * 소셜 미디어 인덱싱 분석
  * 디바이스 데이터 원격 측정 및 모니터링

## Elastic Beanstalk
## ALB (Application Load Balancer)
## Auto Scaling
## EBS
## Amazon EFS (Elastic File System)
## AWS Storage Gateway
## S3
## Glacier
## RDS
## DynamoDB
## ElasticCache
## AWS Application Discovery Service
## AWS Database Migration Service
## AWS Server Migration Service
## AWS Snowball
## Redshift
## Aurora
## Trusted Advisor
## AWS CodeCommit
## AWS CodeBuild
## AWS CodeDeploy
## AWS Codepipeline
## AWS X-Ray
## Amazon CloudWatch
## AWS CloudFormation
## AWS CloudTrail
## AWS Config
## AWS OpsWorks
## AWS Inspector
## AWS Certificate Manager
## AWS CloudHSM
## AWS Key Management Service
## AWS Organizations
## AWS WAF
## Amazon Athena
## Amazon Kinesis
## AWS Data Pipline 
## AWS Glue
## AWS Lex
## AWS Polly
## AWS Rekognition
## AWS Mobile Hub
## AWS Cognito
## AWS Pinpoint
## AWS Step Functions
## AWS API Gateway
## AWS SQS
## AWS SES
