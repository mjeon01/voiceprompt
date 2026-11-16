# 설치와 사용

## 다운로드 확인

[공식 Releases](https://github.com/mjeon01/voiceprompt/releases)에서 OS에 맞는 ZIP과 `SHA256SUMS.txt`를 받으세요.
GitHub의 `Source code` 다운로드에는 앱이 없습니다.

macOS:

```sh
shasum -a 256 VoicePrompt-0.4.1-macos-arm64.zip
```

Windows PowerShell:

```powershell
Get-FileHash .\VoicePrompt-0.5.0-preview.1-windows-x64.zip -Algorithm SHA256
```

출력이 `SHA256SUMS.txt`의 해당 파일과 일치하는지 확인합니다. 해시는 파일 변조·손상을 확인하는 수단이며 게시자 서명을 대체하지 않습니다.

## macOS

1. ZIP을 해제하고 `VoicePrompt.app`을 응용 프로그램 폴더로 옮깁니다.
2. 실행 후 메뉴 막대 아이콘에서 설정을 엽니다.
3. 모델 다운로드를 완료하고 마이크와 손쉬운 사용 권한을 허용합니다.
4. 입력창을 클릭하고 `Control + Shift + Space`를 누릅니다. 말한 뒤 다시 누르면 입력을 요청합니다.

초기 배포는 Apple 공증을 받지 않았습니다. 공식 다운로드와 해시를 확인하고 실행을 결정했다면
차단 후 시스템 설정 → 개인정보 보호 및 보안에서 해당 앱의 **확인 없이 열기** 옵션을 사용할 수 있습니다.
전체 Gatekeeper를 끄거나 보안 설정을 일괄 해제할 필요는 없습니다.
업데이트 후 자동 입력이 막히면 손쉬운 사용에서 해당 앱을 다시 등록합니다.
기존 개발용 설치와 공개 배포의 서명은 달라 권한 재등록이 필요할 수 있습니다.

취소는 `Esc`. 단축키 변경, 녹음 없는 단축키 검사, 마이크 선택과 사용자 용어 추가는 Mac 설정에서 제공합니다.

## Windows

1. Windows 11 x64에서 ZIP을 **전체 압축 해제**합니다. `VoicePrompt.exe`와 DLL·`runtimes` 폴더를 함께 유지합니다.
2. `VoicePrompt.exe`를 실행합니다. .NET은 번들에 포함되어 별도 설치하지 않아도 됩니다.
3. 엔진 로딩 오류가 나면 [Microsoft 공식 Visual C++ x64 런타임](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist)을 설치하고 재실행합니다.
4. **음성 모델 준비**를 누릅니다. 약 488 MB를 다운로드하고 SHA-256을 확인합니다.
5. Windows 설정 → 개인정보 및 보안 → 마이크에서 데스크톱 앱의 마이크 접근을 허용합니다.
6. 대상 앱의 입력창을 클릭하고 `Ctrl + Shift + Space`를 눌러 녹음한 뒤 다시 눌러 완료합니다.

첫 배포는 Authenticode 서명이 없어 SmartScreen 안내가 나올 수 있습니다. 보안 제품을 끄지 말고
공식 배포 파일과 해시를 확인하세요. 조직에서 실행을 제한하면 관리자 정책을 따릅니다.

- Windows 기본 마이크를 사용합니다. 장치 변경은 Windows 소리 설정에서 수행합니다.
- 앱 창의 **녹음 시작** 버튼으로 시작한 경우에는 복사해서 붙여넣습니다. 자동 입력은 대상 창에서 단축키로 시작한 경우에 사용합니다.
- **같은 입력창에 자동으로 입력**을 끄면 항상 수동 복사 방식으로 사용합니다.
- 취소: `Ctrl + Shift + Esc` 또는 앱의 **취소** 버튼. 이미 입력이 시작된 경우 입력된 글자는 자동으로 지우지 않습니다.
- 창의 X는 작업 표시줄 알림 영역으로 숨깁니다. 완전히 종료하려면 **종료**를 선택합니다.
- 단축키가 다른 앱과 충돌하면 창에 안내합니다. 해당 앱의 조합을 해제하고 다시 실행하거나 녹음 버튼을 사용합니다.
- 현재 Windows Preview는 기본 단축키·기본 마이크를 사용합니다. 사용자 단축키 편집과 추가 용어 입력은 아직 없습니다.

## 입력이 안 될 때

녹음 중 창이나 입력 대상이 바뀌면 자동 입력을 중단할 수 있습니다. 비밀번호 입력창에는 자동 입력하지 않습니다.
관리자 권한으로 실행된 앱, 일부 터미널·게임·원격 데스크톱·접근성 정보를 제공하지 않는 입력창은 지원되지 않을 수 있습니다.
결과 복사를 사용하세요. 자동 입력 요청이 성공해도 대상 앱이 실제로 받았는지는 확인해야 합니다.
부분 입력 중 중단되었다면 기존 입력을 확인한 뒤 중복되지 않게 붙여넣으세요.

## 업데이트와 제거

앱을 완전히 종료하고 새 배포 폴더로 교체합니다. 기존 모델은 다음 위치에서 재사용합니다.

| OS | 모델·설정 위치 |
|---|---|
| macOS | `~/Library/Application Support/VoicePrompt/`, 설정은 macOS 사용자 기본 설정 |
| Windows | `%LOCALAPPDATA%\VoicePrompt\models\ggml-small.bin`, `%LOCALAPPDATA%\VoicePrompt\settings.json` |

개발용 Mac 포터블 설치는 앱 옆의 `VoicePromptData`를 사용할 수 있습니다. 일반 공개 ZIP에는 모델이 없습니다.
제거하려면 앱을 종료하고 앱 폴더를 지웁니다. 모델도 없애려면 위 VoicePrompt 전용 폴더를 지우세요.
기존 모델을 지우면 다음 사용 시 다시 다운로드합니다.
