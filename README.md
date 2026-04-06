# ue-docs — Unreal Engine 5.7 Documentation Plugin for Claude Code

Unreal Engine 5.7 프로젝트 작업 시 **공식 문서를 먼저 확인하고, 그 내용을 기반으로 코드를 작성**하는 Claude Code 플러그인.

## 동작 방식

UE 관련 코드 작성 요청이 들어오면 Claude가 자동으로:

1. 관련 카테고리의 공식 문서 검색 (한국어 우선 → 영어 fallback)
2. 검색된 문서 내용을 기반으로 코드 작성
3. 참조한 문서 URL 제공

## 설치

### GitHub에서 직접 설치
```sh
claude plugins add --from https://github.com/JQ-WCoding/ue-docs-plugin
```

### settings.json에 마켓플레이스로 추가
```json
{
  "extraKnownMarketplaces": {
    "ue-docs": {
      "source": { "source": "github", "repo": "JQ-WCoding/ue-docs-plugin" }
    }
  }
}
```

## 사용법

### 자동 동작 (스킬)
UE 관련 작업 요청 시 자동으로 문서를 검색하고 코드를 작성합니다:

```
Enhanced Input으로 WASD 이동을 구현해줘
```
→ Claude가 자동으로 Enhanced Input 문서 검색 후 코드 작성

### 수동 문서 검색 (`/ue-search`)
```
/ue-search Nanite 설정 방법
/ue-search World Partition streaming
```

### API 레퍼런스 검색 (`/ue-api`)
```
/ue-api UCharacterMovementComponent
/ue-api APlayerController
```

### 심층 조사 에이전트 (`@ue-docs-researcher`)
복잡한 다중 시스템 구현이나 아키텍처 설계 시:
```
@ue-docs-researcher GAS와 네트워크 리플리케이션 연동 방법 조사해줘
```

## 지원 문서

- 한국어 (`ko-kr`) 우선, 없으면 영어 (`en-us`) fallback
- UE 5.7 기준 (`?application_version=5.7`)
- C++ API, Blueprint API, Python API 모두 지원

## 팀 공유

이 저장소를 팀원과 공유하면, 각자 위 설치 명령어로 동일한 플러그인을 설치할 수 있습니다.

## 참고

- [UE5.7 공식 문서 (한국어)](https://dev.epicgames.com/documentation/ko-kr/unreal-engine/unreal-engine-5-7-documentation)
- [UE5.7 공식 문서 (영어)](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-5-7-documentation)
- [C++ API 레퍼런스](https://dev.epicgames.com/documentation/en-us/unreal-engine/API/)
