---
description: Look up UE5.7 C++/Blueprint/Python API reference for a class or function. Usage: /ue-api <ClassName or function>
---

UE5.7 API 레퍼런스에서 `$ARGUMENTS`를 검색해줘.

## 검색 절차

1. C++ API 검색: `WebSearch site:dev.epicgames.com/documentation/en-us/unreal-engine/API $ARGUMENTS`
2. Blueprint API (필요 시): `WebSearch site:dev.epicgames.com/documentation/en-us/unreal-engine/BlueprintAPI $ARGUMENTS`
3. 보완 검색: `WebSearch unreal engine 5.7 $ARGUMENTS C++ API reference`

## 결과 형식

- **클래스 계층**: 상속 체인 (e.g., `AActor > APawn > ACharacter`)
- **주요 함수/프로퍼티**: 시그니처, 설명, deprecated 여부
- **소속 모듈**: 헤더 파일 경로 (e.g., `#include "GameFramework/Character.h"`)
- **사용 예시**: 문서에 있는 경우
- **API 레퍼런스 링크**: `https://dev.epicgames.com/documentation/en-us/unreal-engine/API/`

## 제약

- WebFetch 사용 금지
- 반드시 UE5.7 기준으로 확인 (4.x Deprecated API 주의)
