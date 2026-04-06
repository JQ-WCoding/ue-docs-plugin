---
name: ue-docs-reference
description: Use when writing, modifying, or explaining any Unreal Engine code, systems, or configurations - searches official UE5.7 documentation first, then writes code based on the documented API and patterns rather than assumptions
---

# UE5.7 문서 기반 코드 작성

Unreal Engine 관련 작업 요청 시, **반드시 공식 문서를 먼저 확인한 후** 그 내용을 기반으로 코드를 작성한다.

## 이 스킬이 적용되는 상황

다음 키워드/개념이 포함된 작업 요청 시 자동 적용:

- **클래스/컴포넌트**: Actor, Pawn, Character, Controller, Component, GameMode, GameState, PlayerState, HUD, Widget
- **시스템**: Blueprint, Material, Niagara, Animation, Physics, AI, Enhanced Input, Gameplay Ability System (GAS), World Partition, Nanite, Lumen, PCG
- **API**: UPROPERTY, UFUNCTION, UCLASS, TObjectPtr, TWeakObjectPtr, FName, FString, FText, UObject
- **작업 유형**: "UE에서", "언리얼에서", "엔진에서", "블루프린트", "C++ 언리얼"

## 작동 흐름

### 1단계: 문서 카테고리 파악
`skills/ue-docs-reference/ue57-doc-index.md`를 읽어 요청과 관련된 문서 카테고리를 파악한다.

### 2단계: 한국어 문서 검색 (우선)
```
WebSearch: site:dev.epicgames.com/documentation/ko-kr/unreal-engine {관련 키워드}
```

### 3단계: 영어 문서 fallback
한국어 결과가 불충분하거나 없을 경우:
```
WebSearch: site:dev.epicgames.com/documentation/en-us/unreal-engine {relevant keywords}
```

### 4단계: API 레퍼런스가 필요한 경우
정확한 함수 시그니처, 클래스 계층이 필요한 경우:
```
WebSearch: site:dev.epicgames.com/documentation/en-us/unreal-engine/API {ClassName}
```

### 5단계: 문서 기반 코드 작성
- 검색된 문서 내용을 기반으로 코드 작성
- 단순히 링크만 제공하지 않고, **실제 문서 내용을 읽고 적용**
- 참조한 문서 URL을 응답에 포함

## URL 규칙

```
한국어: https://dev.epicgames.com/documentation/ko-kr/unreal-engine/{slug}?application_version=5.7
영어:   https://dev.epicgames.com/documentation/en-us/unreal-engine/{slug}?application_version=5.7
API:    https://dev.epicgames.com/documentation/en-us/unreal-engine/API/{ModuleName}/{ClassName}
```

## 중요 제약사항

- **WebFetch 사용 금지**: UE 문서 사이트는 SPA(Cloudflare 보호)라 WebFetch로 콘텐츠 추출 불가. 반드시 **WebSearch만** 사용.
- **버전 명시**: 검색 시 UE5.7 관련 내용인지 확인. Deprecated API는 피할 것.
- **문서 없이 추측 금지**: 확실하지 않은 API 시그니처는 검색 후 확인.

## 검색 불필요한 경우

- 순수 C++ 문법 (UE와 무관)
- Git, 파일 시스템, 터미널 작업
- 이미 같은 세션에서 문서를 확인한 내용의 재사용
- Python, JavaScript 등 비-UE 작업

## 응답 형식

코드 작성 시:
1. 관련 문서 URL 제시
2. 핵심 내용 요약 (문서에서 확인한 내용)
3. 코드 구현
4. 주의사항 또는 UE5.7에서 변경된 사항

```cpp
// 참조: https://dev.epicgames.com/documentation/ko-kr/unreal-engine/enhanced-input-in-unreal-engine
// Enhanced Input 설정 - UE5.1+ 권장 방식
```
