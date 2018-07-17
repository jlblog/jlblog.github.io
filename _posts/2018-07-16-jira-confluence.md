---
layout: post
title: "JIRA & Confluence 활용"
date: 2015-01-07 21:31:05
description: "사내 업무 시스템에 JIRA와 Confluence를 적용하고 참고할 내용을 정리함.
            2018 Atlassian in Seoul replay 영상을 참고 하였음."
main-class: 'dev'
color: '#637a91'
tags:
- "JIRA"
- "confluence"
twitter_text: ""
introduction: "사내 업무 시스템에 JIRA와 Confluence를 적용하고 참고할 내용을 정리함.
                           2018 Atlassian in Seoul replay 영상을 참고 하였음."
---



# Confluence
* * *
### 활용 사례
 * 문서 관리 : 매뉴얼, 설치가이드
 * 업무 관리 : 회의록, 주간보고 취합 자동화
 * 팀 협업 관리 : 일정 공유, 할당 된 업무 공유
 * 프로젝트 관리 : 주요 이슈 관리
    
### 매크로
 * 70여개의 내장, 플러그인 추가해서 사용 가능
 
### 기능(협업)
 * Follower, Following
 * Like & Comment
 * Mention
 * 동시 편집 **(주간보고 활용)**    
 
  
# JIRA
* * *
### JIRA Software 활용
 * 애자일 방법론
 > 지속적으로 요구사항을 수렴하여 개발 진행, 프로젝트 팀 간 많은 의사소통 필요 
      
 * 제품 매니저 : 프로젝트, 스프린트 및 대형 릴리즈를 위한 타임라인 관리
 * 개발 매니저 : 범위 타임라인 및 제 시간 릴리즈를 위한 리소스 관리
 * 개발자 : 이슈 버그 및 프로젝트와 관련된 모든 업무 요소들의 추적
 * JIRA Administrator
   * 사용자 관리를 통한 인력 관리
   * System 환경 구성
   * Application 상세 정보 관리
   * 플러그인 관리
   * 프로세스 템플릿화(기본제공)
 * Rule & Role
   * **Project Manager** 
     * 이슈 생성, 담당 지정 및 진행 상태 관리
     * 보드 관리(스크럼, 칸반), 대시보드 관리
   * **Project Member**
     * 이슈 생성 및 진행, 이슈의 종료, 보드에서 이슈 진행
  * JIRA Project Board
    * Scrum board : 반복주기(Sprint)에 따라 수행되는 issue를 관리. 백로그(모든 요구사항) 개발주기내 이슈를 진행
    * Kanban board : 제품 릴리즈 기반의 상태 별 issue를 관리
    * Dashboard : 진행사항을 효율적으로 보여줌 (가젯을 이용한 레이아웃 구성)
  * JIRA 연동 : 요구사항 정의서 등 링크를 통한 JIRA 연동
    
<div class="mermaid" style="text-align:center;">
graph LR
A[Confluence] -- 요구사항정의서 --> B(JIRA)
B -- 기획 확인 --> A
</div>
      
### DevOps
 > 개발자와 운영 및 관련자의 의사소통, 협업, 융합을 강조한 소프트웨어 개발 방법론.
  DevOps는 개발과 운영 간의 유기적 연계를 통해 Agile 방식의 업무를 수행.
 
 * Bamboo와 연결해서 자동 배포하는 기능
 * 자동화 릴리즈 진행(Bamboo)
 * JIRA, Bitbucket, Bamboo 개발 사이클 구성 가능
 * **JIRA, Github, Zenkins로 대체 가능**하나 플러그인 설치 및 추가 구매비용이 발생할 수 있음                      

### 개발 활용
 * 각 솔루션 매뉴얼이나 가이드를 Confluence에 업로드 후 링크를 통해 접근
 * 솔루션 별 회의록 작성 (업무 할당 가능)
 * 동시 편집이 가능한 주간보고 활용 (보고서 형태로 회의시 사용 가능)
 * 달력을 이용한 개발 일정 공유 (플러그인 설치) 
 * Zenkins 사용시 JIRA, GitHub, Zenkins 개발 사이클 구성 (단계적으로 적용 필요)    
 * JIRA, Bitbucket, Bamboo 조합을 추천  

<div class="mermaid" style="text-align:center;">
sequenceDiagram
    participant Confluence
    participant JIRA
    participant GitHub
    participant Zenkins
    loop 이슈 등록
        Confluence-->>JIRA: 회의록(업무할당)
        Confluence->>JIRA: 요구사항정의서
        JIRA-->>Confluence: 프로젝트 정보 확인
    end
    JIRA-->GitHub: Sourcetree
    GitHub-->Zenkins: (Bitbucket + Bamboo)    
    loop Version Control
        JIRA->>GitHub: Commit/Pull Request/Merge
        GitHub->>JIRA: 이슈 상태 변경                  
    end    
    loop 자동 배포
        JIRA->Zenkins: Test
        JIRA->Zenkins: Build
        JIRA->Zenkins: Deploy
    end 
</div>
<br>
  
## 참고
* [https://confluence.curvc.com/pages/viewpage.action?pageId=2031867](https://confluence.curvc.com/pages/viewpage.action?pageId=2031867 "JIRA 가이드")
* [http://atlassiankorea.com/replay](https://youtube.com/watch?v=vB9s-QgbFwk&list=PLckYD6YhlHdb7NZatzm-svFtB81SjhwPu "Atlassian in Seoul -youtube")

