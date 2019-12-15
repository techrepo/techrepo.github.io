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

# AWS 글로벌 인프라 (AWS 호스팅)
#### 리전
- 2개 이상의 가용 영역을 호스팅하는 지리 영역
- 리전은 서로 완전히 독립된 엔터티
- 한 리전의 리소스는 다른 지전으로 자도 복제되지 않음
#### 가용 영역 (AZ)
- 특정 리전 내에 존재하는 데이터 센터들의 모음
- 각 가용 영역들은 서로 격리되어 있지만 지연 시간이 짧은 링크로 연결
- 물리적으로 구분된 독립적 인프라
- 물리적, 논리적 분리
- 별도의 무정전 전원 공급 장치(UPS), 현장 예비 발전기, 냉각 장비, 네트워킹 및 연결 수단
- 독립적인 전력 획사의 서로 다른 전력망을 통해 전력 공급
- 다중 AZ에 결쳐 프로비저닝 할 것을 권장
#### 엣지 로케이션
- CloudFront라고 하는 CDN호스팅
- 여러 엣지 로케이션과 리전으로 구성된 글로벌 네트워크를 활용하면 보다 빠른 컨텐츠 전송 가능
- 리전 및 가용 영역과 비슷하게 인구 밀도가 높은 지역에 위치

# VPC
# AWS Direct Connect
# 보안 그룹
# Amazon Lightsail
# AWS Lambda
# Elastic Beanstalk
# ALB (Application Load Balancer)
# Auto Scaling
# EBS
# Amazon EFS (Elastic File System)
# AWS Storage Gateway
# S3
# Glacier
# RDS
# DynamoDB
# ElasticCache
# AWS Application Discovery Service
# AWS Database Migration Service
# AWS Server Migration Service
# AWS Snowball
# Redshift
# Aurora
# Trusted Advisor
# AWS CodeCommit
# AWS CodeBuild
# AWS CodeDeploy
# AWS Codepipeline
# AWS X-Ray
# Amazon CloudWatch
# AWS CloudFormation
# AWS CloudTrail
# AWS Config
# AWS OpsWorks
# AWS Inspector
# AWS Certificate Manager
# AWS CloudHSM
# AWS Key Management Service
# AWS Organizations
# AWS WAF
# Amazon Athena
# Amazon Kinesis
# AWS Data Pipline 
# AWS Glue
# AWS Lex
# AWS Polly
# AWS Rekognition
# AWS Mobile Hub
# AWS Cognito
# AWS Pinpoint
# AWS Step Functions
# AWS API Gateway
# AWS SQS
# AWS SES
