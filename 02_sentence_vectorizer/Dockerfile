FROM python:3.11-slim

# 자바 설치에 필요한 기본 유틸리티 및 OpenJDK 17 설치
RUN apt-get update && apt-get install -y --no-install-recommends \
    openjdk-17-jdk \
    procps \
    && rm -rf /var/lib/apt/lists/*

# KoNLPy가 인식할 수 있도록 JAVA_HOME 경로 강제 지정
ENV JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
ENV PATH="$JAVA_HOME/bin:$PATH"

WORKDIR /app

# 파이썬 패키지 설치
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 소스 코드 복사
COPY . .

# FastAPI 실행
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "10000"]
