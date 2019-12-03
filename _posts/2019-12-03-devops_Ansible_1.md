---
title: "DevOps_Ansible_1"
header:
 overlay_image: /assets/images/overlayimage.jpg
categories:
  - DevOps
tags:
  - Ansible
use_math: true
toc: true
toc_label: "페이지 주요 목차"
toc_sticky: true
---
Ansible이란 무엇일까?

## 1. Ansible이란?
Ansible은 Infrastucture as code를 지향하는 **자동화 관리도구**이다.

Ansible을 구동하는 모듈 및 라이브러리는 Python기반이며,
YAML 포맷을 기반으로 플래이북을 실핼시켜서 자동화를 구현하고,
Ad-Hoc 모드로 모듈을 실행시켜 상태를 조회해 볼 수 있다.

또한, Ansible은 SSH 기반으로 Target Host에 `Agentless`방식으로 자동화를 구성 관리한다.
기존의 동작방식인 Pull방식에서 Agentless기반의 `Push` 방식으로 동작하기 때문에 설치와 구성관리가 편리한 장점이 있다.


## 2. Ansible 특징
- 빠른 SSH통신, 빠른 provision이 가능
- 추후 상용 환경에서 사용할 때 agent 기반이면 방화벽 이슈, agent 데몬 관리라는 불편한 점이 존재 (agent 방식은 확장성, 대규모 provision을 할 경우 매우 효과적이지만 서버와 통신하는 부분이 고도화되기 때문에 빠르고 간단한 provision을 할 수 없음)
- 자동 배포 환경이 쉬움
- 멱등성
- playbook
- ad-hoc

## 3. Ansible 사용해보기

### 3.1 사용 환경 준비
### 3.2 중요 개념
#### 3.2.1 인벤터리 (Inventory)
#### 3.2.2 플레이북 (playbook)
#### 3.2.3 모듈 (module)

### 3.3 기타 개념
#### 3.3.1 멱등성
멱등성이란 똑같은 작업을 몇번을 수행해도 동일한 결과를 얻을 수 있는 것을 의미한다.
모듈 실행 시 결과를 state로 정의함으로써 최종적으로 존재해야 하는 환경을 명시한다.
해당 state가 만족된다면 앤서블은 다른 작업을 하지 않고 task를 종료한다.

예를 들어, yum 모듈을 통해 `state:installed`로 명시된 플레이북이 실행될 때, 
해당 패키지가 이미 설치되어 있다면 해당 task는 아무런 동작도 하지 않고 `success`로 처리후 종료된다.


#### 3.3.2 Ad-Hoc
Ad-Hoc 은 임시적으로 수행하는 의미다. Ansible의 playbook을 작성하여 수행하는 것이 아니라 임시적으로 작업을 수행하기 위해서 사용하는 방법이다.

## 4. Ansible 한계
- 시스템의 초기 설치 수행이 불가능 (kickstart, pxe등을 사용하여야 함)
