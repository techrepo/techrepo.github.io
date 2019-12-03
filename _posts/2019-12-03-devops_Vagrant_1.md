---
title: "DevOps_Vagrant_1"
header:
 overlay_image: /assets/images/overlayimage.jpg
categories:
  - DevOps
tags:
  - Vagrant
use_math: true
toc: true
toc_label: "페이지 주요 목차"
toc_sticky: true
---
Vagrant란 무엇일까?

## Vagrant란?
Vagrant는 **로컬 환경에서 가상화 관리를 가능하게 해주는 도구** 이다.

Vagrant를 사용하기 위해서는 반드시 가상화 도구(Virtual Box, VMware, Hyper-v 등) 필요하다.
Vagrant는 마치 **프로비져닝을 담당하는 도구**로 동작하며
가상화 도구 **(Virtural Box, VMware, Hyper-v)을 제어하면서 일괄 배포**하는 역할을 한다.

Vagrant의 핵심은 **Vagrantfile** 이다.

## Vagrnat 명령어

**VM 생성, 구동**  

명령어|설명
-|-
vagrant -v|설치 후 버전 확인
vagrant init <boxpath>|vm 생성
vagrant up|vagrant 생성
vagrant resume|vm suspend
vagrant provision|강제로 reprovision
vagrant reload|vagrant VM 재구동
vagrant status|vagrant VM 상태 확인

**VM 접속, 정지, 삭제**  

명령어|설명
-|-
vagrant ssh|vagrant ssh 접속 (vm1대는 이름 필요없음)
vagrant ssh <boxpath>|ssh 접속하기 위한 box name
vagrant halt <boxname>|vm 셧다운
vagrant suspend <boxname>|vm suspend
vagrant destroy|vm 삭제
vagrant destroy -f|vm 강제 삭제
