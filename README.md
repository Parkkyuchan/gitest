# 리걸AI 서비스 (Legal AI Service)

AI 기반 법률 상담 및 문서 분석 서비스입니다.

## 프로젝트 구조

```
law_service/
├── law-service-frontend/     # React 프론트엔드
└── law-service-backend/      # Spring Boot 백엔드
```

## 기술 스택

### 프론트엔드
- React 19.1.1
- Tailwind CSS
- React Router
- Axios
- Lucide React (아이콘)
- React Dropzone (파일 업로드)
- React Markdown (마크다운 렌더링)

### 백엔드
- Spring Boot 3.2.0
- Spring Data JPA
- Spring Security
- H2 Database (개발용)
- PostgreSQL (프로덕션용)
- Spring AI (OpenAI 통합)
- Apache PDFBox (PDF 처리)
- Apache POI (Word 문서 처리)

### AI/ML
- OpenAI GPT-3.5-turbo
- RAG (Retrieval-Augmented Generation)
- 벡터 데이터베이스 (PgVector)

## 주요 기능

### 1. 법률 상담 채팅
- AI 기반 법률 질문 답변
- 실시간 채팅 인터페이스
- 채팅 세션 관리
- 컨텍스트 기반 답변

### 2. 문서 분석
- PDF, DOCX, TXT 파일 지원
- 자동 텍스트 추출
- AI 기반 문서 분석
- 위험도 평가
- 핵심 포인트 추출

### 3. 대시보드
- 통계 및 분석 데이터
- 최근 활동 모니터링
- 문서 관리
- 사용량 추적

## 설치 및 실행

### 프론트엔드 실행

```bash
cd law-service-frontend
npm install
npm start
```

프론트엔드는 http://localhost:3000 에서 실행됩니다.

### 백엔드 실행

1. 환경 변수 설정:
```bash
export OPENAI_API_KEY=your-openai-api-key-here
```

2. Maven으로 실행:
```bash
cd law-service-backend
./mvnw spring-boot:run
```

백엔드는 http://localhost:8080 에서 실행됩니다.

## API 문서

### 문서 업로드
```
POST /api/documents/upload
Content-Type: multipart/form-data

파일: [업로드할 파일]
```

### 채팅
```
POST /api/chat
Content-Type: application/json

{
  "message": "사용자 메시지",
  "sessionId": "세션 ID (선택사항)"
}
```

### 대시보드 통계
```
GET /api/dashboard/stats
```

## 환경 설정

### 백엔드 설정 (application.yml)
```yaml
spring:
  ai:
    openai:
      api-key: ${OPENAI_API_KEY}
      chat:
        options:
          model: gpt-3.5-turbo
          temperature: 0.7
```

### 프론트엔드 설정
백엔드 API URL은 기본적으로 `http://localhost:8080`으로 설정되어 있습니다.

## 개발 가이드

### 새로운 기능 추가

1. **백엔드**: 
   - 엔티티 클래스 생성
   - Repository 인터페이스 생성
   - Service 클래스 구현
   - Controller 클래스 구현

2. **프론트엔드**:
   - React 컴포넌트 생성
   - API 호출 함수 구현
   - 라우팅 설정

### 데이터베이스 마이그레이션

H2 콘솔: http://localhost:8080/h2-console
- JDBC URL: jdbc:h2:mem:testdb
- Username: sa
- Password: password

## 라이센스

이 프로젝트는 MIT 라이센스 하에 배포됩니다.
