# ue-docs — Unreal Engine 5.7 Documentation Plugin for Claude Code

Unreal Engine 5.7 프로젝트 작업 시 **공식 문서를 먼저 확인하고, 그 내용을 기반으로 코드를 작성**하는 Claude Code 플러그인.

## 동작 방식

UE 관련 코드 작성 요청이 들어오면 Claude가 자동으로:

1. 관련 카테고리의 공식 문서 검색 (한국어 우선 → 영어 fallback)
2. 검색된 문서 내용을 기반으로 코드 작성
3. 참조한 문서 URL 제공

---

## 설치

Claude Code 플러그인 시스템은 **plugin**과 **marketplace**를 구분합니다.  
이 저장소는 plugin(`plugin.json`)이므로, 직접 `plugins install`로는 설치할 수 없습니다.  
아래 절차에 따라 **로컬 marketplace를 경유**하여 설치하세요.

### 1단계: 저장소 클론

```sh
git clone https://github.com/JQ-WCoding/ue-docs-plugin.git
```

### 2단계: 임시 marketplace 디렉터리 생성

```sh
mkdir -p /tmp/ue-docs-marketplace/.claude-plugin
```

> Windows(Git Bash)에서 `/tmp`는 `C:\Users\<사용자>\AppData\Local\Temp`로 매핑됩니다.

### 3단계: marketplace.json 작성

아래 내용을 `/tmp/ue-docs-marketplace/.claude-plugin/marketplace.json`에 저장합니다:

```json
{
  "name": "ue-docs-marketplace",
  "owner": {
    "name": "JQ-WCoding"
  },
  "metadata": {
    "description": "Unreal Engine 5.7 documentation auto-reference plugin",
    "version": "1.0.0"
  },
  "plugins": [
    {
      "name": "ue-docs",
      "source": {
        "source": "url",
        "url": "https://github.com/JQ-WCoding/ue-docs-plugin.git"
      },
      "description": "Unreal Engine 5.7 official documentation auto-reference. Searches and reads UE docs before writing code.",
      "version": "1.0.0"
    }
  ]
}
```

또는 한 번에 실행:

```sh
cat > /tmp/ue-docs-marketplace/.claude-plugin/marketplace.json << 'EOF'
{
  "name": "ue-docs-marketplace",
  "owner": { "name": "JQ-WCoding" },
  "metadata": { "description": "Unreal Engine 5.7 documentation auto-reference plugin", "version": "1.0.0" },
  "plugins": [
    {
      "name": "ue-docs",
      "source": { "source": "url", "url": "https://github.com/JQ-WCoding/ue-docs-plugin.git" },
      "description": "Unreal Engine 5.7 official documentation auto-reference.",
      "version": "1.0.0"
    }
  ]
}
EOF
```

### 4단계: marketplace 등록

```sh
claude plugins marketplace add /tmp/ue-docs-marketplace
```

> Windows(Git Bash)에서 경로가 인식되지 않으면 Windows 절대경로를 사용합니다:
> ```sh
> claude plugins marketplace add "C:/Users/<사용자>/AppData/Local/Temp/ue-docs-marketplace"
> ```

### 5단계: 플러그인 설치

```sh
claude plugins install ue-docs
```

설치 결과 확인:

```sh
claude plugins list
```

다음과 같이 출력되면 성공입니다:

```
❯ ue-docs@ue-docs-marketplace
  Version: 1.0.0
  Scope: user
  Status: ✔ enabled
```

---

## 배경: plugin vs marketplace

| 개념 | manifest 파일 | 역할 |
|------|--------------|------|
| **Plugin** | `.claude-plugin/plugin.json` | 실제 스킬·에이전트·명령어를 담는 단위 |
| **Marketplace** | `.claude-plugin/marketplace.json` | 여러 plugin을 목록화하는 카탈로그 |

`claude plugins install`은 marketplace에 등록된 plugin만 설치할 수 있습니다.  
이 저장소는 plugin이므로, 위 절차처럼 래퍼 marketplace를 만들어 경유해야 합니다.

---

## 사용법

### 자동 동작 (스킬)
UE 관련 작업 요청 시 Claude가 자동으로 문서를 검색하고 코드를 작성합니다:

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

---

## 지원 문서

- 한국어 (`ko-kr`) 우선, 없으면 영어 (`en-us`) fallback
- UE 5.7 기준 (`?application_version=5.7`)
- C++ API, Blueprint API, Python API 모두 지원

---

## 참고

- [UE5.7 공식 문서 (한국어)](https://dev.epicgames.com/documentation/ko-kr/unreal-engine/unreal-engine-5-7-documentation)
- [UE5.7 공식 문서 (영어)](https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-5-7-documentation)
- [C++ API 레퍼런스](https://dev.epicgames.com/documentation/en-us/unreal-engine/API/)
