# Git 주간 리포트 시스템

매주 자동으로 Git 커밋 활동을 요약하여 메일로 발송하는 시스템입니다.

## 🚀 기능

- 매주 월요일 자동으로 지난 7일간의 커밋 활동 분석
- 커밋 통계, 개발자별 활동, 상세 커밋 내역 포함
- 깔끔한 HTML 형식의 메일 리포트

## ⚙️ 설정 방법

### 1. GitHub Repository Secrets 설정

GitHub 저장소의 Settings > Secrets and variables > Actions에서 다음 secrets를 추가하세요:

- `EMAIL_USERNAME`: 발송용 Gmail 계정 (예: your-email@gmail.com)
- `EMAIL_PASSWORD`: Gmail 앱 비밀번호 (2단계 인증 필요)
- `EMAIL_TO`: 리포트를 받을 메일 주소 (예: team@company.com)
- `EMAIL_FROM`: 발송자 이름 (예: "Git Report System <noreply@company.com>")

### 2. Gmail 설정

1. Gmail 계정에서 2단계 인증 활성화
2. 앱 비밀번호 생성 (보안 > 2단계 인증 > 앱 비밀번호)
3. 생성된 16자리 앱 비밀번호를 `EMAIL_PASSWORD`에 설정

### 3. 스케줄 변경 (선택사항)

`.github/workflows/weekly-report.yml` 파일의 cron 표현식을 수정하여 발송 시간을 변경할 수 있습니다:

```yaml
schedule:
  - cron: '0 0 * * SUN'  # 매주 일요일 UTC 자정 (한국시간 월요일 오전 9시)
```

## 📧 리포트 내용

- 📊 커밋 통계 (총 커밋 수, 활동 개발자 수)
- 👥 개발자별 활동 현황
- 📝 상세 커밋 내역 (해시, 작성자, 메시지)
- 📁 파일 변경 통계

## 🔧 수동 실행

GitHub Actions 탭에서 "Weekly Git Report" 워크플로우를 찾아 "Run workflow" 버튼으로 수동 실행 가능합니다.

## 📋 요구사항

- GitHub 저장소
- Gmail 계정 (또는 SMTP 서버)
- GitHub Actions 활성화

## 🚀 사용법

1. GitHub에서 Actions 탭 확인
2. "Weekly Git Report" 워크플로우에서 "Run workflow" 클릭