# Erduo B-roll Loop Engineering

**원본 SRT와 디자인을 의미 있는 움직임과 편집 가능한 소스를 갖춘 B-roll로 만듭니다.**

[简体中文](README.md) · [English](README.en.md) · [日本語](README.ja.md) · 한국어 · [繁體中文](README.zh-TW.md)

> `main`은 영상 품질을 우선하는 역할별 제작 흐름을 사용합니다. 최신 버전 Release는 여전히 [v1.0.1](https://github.com/erduo1998-cell/erduo-broll-loop-engineering/releases/tag/v1.0.1)이며 해당 배포 파일은 이전 흐름입니다. 새 흐름은 현재 저장소에서 설치하세요.

## 제작 흐름

원본 SRT + 디자인 + 선택 자료 → 독립 감독 → 새 컨텍스트의 챕터 제작자 → 스크립트 렌더링과 독립 영상 검토 → 원래 제작자의 부분 수정 → 최종 샷, 전체 미리보기와 편집 가능한 프로젝트.

짧은 영상도 감독·제작·미적 검토의 컨텍스트를 분리합니다. 제작자에게는 전체 원본, 간결한 공통 방향, 담당 샷과 앞뒤 연결 정보만 전달합니다. 부모 대화 기록이나 전체 Skill 목록을 넘기지 않습니다. 긴 영상은 이야기의 연속성에 따라 분담하고 자료 담당자는 필요할 때 추가합니다.

시간 검사, 렌더링, 디코딩, 캐시와 조합은 부모가 스크립트로 실행합니다. 실제 화면을 보고 수정하며 기술 검사 성공을 미적 승인으로 취급하지 않습니다. 시간이나 Token을 줄이려고 필요한 시안과 수정을 생략하지 않습니다. 사용자가 지정한 검토·중지 지점을 지킵니다.

세 가지 간결한 모션 참고와 실행 가능한 원본 예제를 제공합니다. 고정 색상이나 종이 카드 템플릿이 아닙니다. 대상을 알아볼 수 있는 자료를 사용하고 SVG는 명확한 관계, 차트, 마스크와 경로에 활용합니다.

## 설치

```sh
git clone https://github.com/erduo1998-cell/erduo-broll-loop-engineering.git
cd erduo-broll-loop-engineering
./Install.command
```

고정 버전 HyperFrames, 브라우저, FFmpeg 및 Skill 링크를 준비합니다. 설치 폴더를 유지하고 완료 후 Codex 또는 Claude Code를 다시 시작하세요. v1.0.1 배포 파일은 동봉 README를 따릅니다.

```sh
node scripts/doctor.mjs
node scripts/uninstall.mjs
```

제거 시 사용자 데이터는 기본적으로 보존됩니다.

## 첫 요청

```text
erduo-broll-loop-engineering으로 이 원본 SRT와 디자인을 B-roll로 만들어 주세요.
감독, 챕터 제작자, 영상 검토자를 서로 다른 컨텍스트로 실행하세요.
영상 품질을 우선하고 실제 결과를 확인·수정한 뒤 전체 미리보기를 전달하세요.
```

편집 가능한 HTML/CSS/JS, 자료 출처, 순서가 정해진 H.264 샷과 전체 미리보기를 제공합니다. 기본 최종 출력은 무음 3840×2160, 30fps입니다. 사용자 지정 규격이 우선이며 자막 전체와 음악은 자동 추가하지 않습니다.

## 검증 범위

동일 입력의 32초 비교에서 독립 Sol의 키프레임·장면 연결 검토는 새 흐름을 선호했고 사용자도 선택했습니다. 양쪽 모두 1080p/30fps 실제 디코딩을 통과했습니다. S02 변경은 8.569초에 반영됐고 나머지 세 샷은 바이트 단위로 동일했습니다.

**시간·Token 절약은 아직 입증되지 않았습니다.** 모델 단계는 새 흐름 611.281초, 비교 흐름 325.136초였습니다. 환경 장애와 불필요한 검색을 포함하므로 정확한 전체 제작 속도 비교가 아닙니다. 작업 도구는 입력을 정리하지만 호스트가 주입한 모든 컨텍스트를 제거하거나 샌드박스를 강제하지 않습니다. [검증 기록](docs/LEAN-WORKFLOW-VALIDATION.md).

기존 Recipe/runtime-plan v1–v4와 명시적인 Remotion/hybrid 요청은 [이전 흐름](erduo-broll-loop-engineering/references/legacy-production.md)을 유지합니다. 긴 영상, Windows, 편집기 GUI 및 백엔드 간 시각적 일치는 새 흐름에서 검증하지 않았습니다. 152개 Shotcraft 카드는 선택 참고 자료이며 검증된 컴포넌트 152개가 아닙니다.

## 개발

```sh
npm test
npm run task:creative -- --project /path/to/project --role director
npm run render:lean -- --project /path/to/project --quality draft
```

[제작 명령](erduo-broll-loop-engineering/references/lean-production.md) · [모션 참고](erduo-broll-loop-engineering/references/motion-patterns.md) · [개인정보](PRIVACY.md) · [지원 범위](SUPPORT-MATRIX.md) · [변경 기록](CHANGELOG.md) · [MIT](LICENSE)
