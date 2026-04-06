---
description: Search UE5.7 official documentation by topic. Usage: /ue-search <topic>
---

UE5.7 공식 문서에서 `$ARGUMENTS` 관련 내용을 검색하고 정리해줘.

## 검색 절차

1. `skills/ue-docs-reference/ue57-doc-index.md`를 읽어 관련 카테고리 파악
2. 한국어 문서 검색: `WebSearch site:dev.epicgames.com/documentation/ko-kr/unreal-engine $ARGUMENTS`
3. 결과가 불충분하면 영어 fallback: `WebSearch site:dev.epicgames.com/documentation/en-us/unreal-engine $ARGUMENTS`
4. API 시그니처가 필요하면: `WebSearch site:dev.epicgames.com/documentation/en-us/unreal-engine/API $ARGUMENTS`

## 결과 형식

- 관련 문서 링크 (한국어 우선, `?application_version=5.7` 파라미터 포함)
- 핵심 내용 요약
- 코드 예시 (있는 경우)
- UE5.7에서 주의할 사항

## 제약

- WebFetch 사용 금지 (SPA 사이트라 콘텐츠 추출 불가)
- WebSearch만 사용
