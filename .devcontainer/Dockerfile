# 1. 고성능 Python 3 기본 이미지 사용
FROM python:3.11-slim

# 빌드 인자: LLM 모델 및 API 설정 (기본값은 Claude)
ARG LLM_MODEL=claude
ARG LLM_API_KEY=
ARG LLM_API_ENDPOINT=

# 환경 변수: 컨테이너 내부에서 사용
ENV LLM_MODEL=${LLM_MODEL}
ENV LLM_API_KEY=${LLM_API_KEY}
ENV LLM_API_ENDPOINT=${LLM_API_ENDPOINT}

# 2. 필수 시스템 패키지 및 Node.js 설치 (Claude Code 구동용)
RUN apt-get update && apt-get install -y \
    curl \
    git \
    ca-certificates \
    && curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs \
    && rm -rf /var/lib/apt/lists/*

    # 3. 최신 Python 패키지 관리자(uv) 설치 (권장)
    ADD https://astral.sh/uv/install.sh /install.sh
RUN chmod +x /install.sh && /install.sh && rm /install.sh
ENV PATH="/root/.local/bin/:${PATH}"

# 4. Claude Code 전역 설치
RUN npm install -g @anthropic-ai/claude-code
