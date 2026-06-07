# LLM 모델 설정 가이드

이 Dev Container에서 다른 LLM 모델을 사용하는 방법입니다.

## 사용 방법

### 방법 1: 환경 변수로 설정

터미널에서 환경 변수를 설정하고 컨테이너를 재빌드하세요:

```bash
# macOS/Linux
export LLM_MODEL=gpt-4
export LLM_API_KEY=your_api_key_here
export LLM_API_ENDPOINT=https://api.openai.com/v1

# 또는 다른 모델
export LLM_MODEL=ollama
export LLM_API_ENDPOINT=http://localhost:11434
```

### 방법 2: VSCode 설정 파일

`.vscode/settings.json` 또는 `.devcontainer/devcontainer.json`에서 설정:

```json
{
  "containerEnv": {
    "LLM_MODEL": "gpt-4",
    "LLM_API_KEY": "your_api_key",
    "LLM_API_ENDPOINT": "https://api.openai.com/v1"
  }
}
```

## 지원 모델 예시

### Anthropic Claude
```bash
export LLM_MODEL=claude
export LLM_API_KEY=sk-ant-...
```

### OpenAI GPT
```bash
export LLM_MODEL=gpt-4
export LLM_API_KEY=sk-...
export LLM_API_ENDPOINT=https://api.openai.com/v1
```

### Ollama (로컬 모델)
```bash
export LLM_MODEL=ollama
export LLM_API_ENDPOINT=http://host.docker.internal:11434
```

### 다른 OpenAI 호환 API
```bash
export LLM_MODEL=custom-model
export LLM_API_KEY=your_key
export LLM_API_ENDPOINT=https://your-api-endpoint.com/v1
```

## 컨테이너 내부에서 확인

컨테이너가 시작된 후 환경 변수를 확인:

```bash
echo $LLM_MODEL
echo $LLM_API_ENDPOINT
```

## 주의사항

- API 키는 절대로 커밋하지 마세요
- `.env` 파일을 사용하여 키를 관리하는 것을 권장합니다
- 컨테이너를 재빌드하려면 VSCode에서 Dev Container를 다시 빌드하세요