# Ylog — 누구나 블로그를 만들어 글을 쓰고 나누는 서비스

회원마다 블로그 하나. 마크다운 글쓰기, 주제별 둘러보기, 댓글·구독, 블로그 통계, 관리자 기능까지 기획부터 배포까지 혼자 진행한 프로젝트입니다.

## 저장소

| 저장소 | 내용 |
|---|---|
| [**blog-app**](https://github.com/my-blog-home/blog-app) | 서버(Spring Boot)·화면(React) 코드, 배포 스크립트. 기술 선택 이유·설계 결정·트러블슈팅·성능 개선은 [README](https://github.com/my-blog-home/blog-app#readme) |
| [**docs**](https://github.com/my-blog-home/docs) | 코드보다 먼저 쓴 요구사항과 설계 문서 (GitHub Spec Kit) |

## 기술 스택

![Java](https://img.shields.io/badge/Java_21-ED8B00?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot_3.5-6DB33F?logo=springboot&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL_16-4169E1?logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis_7-DC382D?logo=redis&logoColor=white)
![React](https://img.shields.io/badge/React_18-61DAFB?logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?logo=githubactions&logoColor=white)

## 이렇게 만들었습니다

- **문서 먼저** — Spec Kit으로 원칙(constitution) → 사용자 시나리오·요구사항(spec) → 기술 결정 기록(R-01~R-17) → 데이터·API·화면 설계 → 할 일 목록 순서로 정한 뒤 개발했습니다.
- **Git Flow** — `develop`에 기능 브랜치를 모으고 `release`·`hotfix`에서만 버전을 올려 `main`으로 내보냅니다.
- **CI/CD** — PR마다 테스트·도커 빌드, `main`에 병합되면 테스트 → 이미지 빌드 → 서버 배포 → 릴리스 노트 공지·GitHub 릴리스까지 자동입니다. 배포는 Nginx 앞단의 블루-그린 방식으로 사이트를 멈추지 않습니다.
- **성능은 측정으로** — 자주 읽히는 순위를 Redis에 캐싱하고 전후를 쟀습니다. 실시간 인기 검색어 처리량 약 370배, 지금 핫한 글·인기 블로거는 실행 계획으로 진짜 병목(색인을 못 쓰는 날짜 조건)을 찾아 고친 뒤 캐싱해 약 25~33배.
- **규칙은 서버가** — 비공개 글 노출 조건을 한곳에 모으고, 권한·인증번호·로그인 잠금·계정 존재 비노출을 통합 테스트로 지킵니다.
