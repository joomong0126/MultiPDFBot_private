# 📚 벡터 DB 기반 챗봇

PDF 파일들을 벡터 DB로 변환하여 보안을 강화한 AI 챗봇입니다. PDF 원본 파일은 GitHub에 업로드하지 않고, 벡터 DB만 사용하여 질문에 답변합니다.

## ✨ 주요 기능

- 🔒 **보안 강화**: PDF 원본 파일은 GitHub에 업로드하지 않음
- 📊 **벡터 DB 기반**: PDF → 벡터 DB 변환 후 DB만 사용
- 🔍 **지능형 검색**: 관련 정보를 정확하게 검색하여 답변
- 📚 **출처 표시**: 답변의 출처를 명확히 표시
- 🧠 **통합 분석**: 여러 문서의 정보를 종합하여 답변

## 🚀 설치 및 실행

### 1. 저장소 클론
```bash
git clone https://github.com/your-username/chatbot_five_pdf.git
cd chatbot_five_pdf
```

### 2. 의존성 설치
```bash
pip install -r requirements.txt
```

### 3. 환경 변수 설정
`.env` 파일을 생성하고 OpenAI API 키를 설정하세요:
```
OPENAI_API_KEY=your_openai_api_key_here
```

### 4. 벡터 DB 생성 (1회만 실행)
PDF 파일들이 있는 상태에서 벡터 DB를 생성합니다:
```bash
python create_vector_db.py
```

### 5. PDF 파일 이동 (보안)
벡터 DB 생성 후 PDF 파일들을 안전한 곳으로 이동하거나 삭제합니다.

### 6. 챗봇 실행
```bash
streamlit run pdf_final.py
```

## 📋 사용 단계

### Step 1: 벡터 DB 생성
```bash
# PDF 파일들이 있는 상태에서 실행
python create_vector_db.py
```

**출력 예시:**
```
============================================================
📚 PDF to Vector DB 변환기
============================================================
🚀 PDF 파일들을 벡터 DB로 변환을 시작합니다...
📁 발견된 PDF 파일: 5개
📄 BPS-400S 스텐바이 5V 분석.pdf 처리 중...
✅ BPS-400S 스텐바이 5V 분석.pdf 처리 완료
...
📄 총 25개의 문서 페이지를 수집했습니다.
🔪 텍스트 청킹 중...
📄 150개의 텍스트 청크를 생성했습니다.
🧠 임베딩 모델 로딩 중...
💾 벡터 DB 생성 중...
✅ 벡터 DB 생성이 완료되었습니다!
📊 생성된 청크 수: 150
📁 저장 위치: ./vector_db
```

### Step 2: PDF 파일 보안 처리
벡터 DB 생성 후 PDF 파일들을 안전한 곳으로 이동:
```bash
# PDF 파일들을 별도 폴더로 이동
mkdir secure_pdfs
mv *.pdf secure_pdfs/
```

### Step 3: 챗봇 실행
```bash
streamlit run pdf_final.py
```

## 📖 사용법

1. **벡터 DB 상태 확인**: 사이드바에서 벡터 DB 로드 상태 확인
2. **질문하기**: 채팅창에 벡터 DB에 저장된 문서 내용에 대한 질문 입력
3. **답변 확인**: AI가 벡터 DB의 정보를 기반으로 답변 제공
4. **출처 확인**: 답변 후 참고한 문서 정보 확인

## 🔒 보안 고려사항

- **PDF 파일**: GitHub에 업로드되지 않음 (`.gitignore`에 포함)
- **벡터 DB**: 로컬에서만 저장 및 사용
- **API 키**: `.env` 파일에 안전하게 저장
- **메타데이터**: 원본 파일 경로 정보는 벡터 DB에 저장되지만 파일 자체는 없음

## 📁 프로젝트 구조

```
chatbot_five_pdf/
├── pdf_final.py              # 벡터 DB 기반 챗봇
├── create_vector_db.py       # PDF → 벡터 DB 변환 스크립트
├── requirements.txt          # Python 의존성 목록
├── .gitignore               # 보안 강화된 gitignore
├── README.md                # 프로젝트 설명서
├── .env                     # 환경 변수 파일 (사용자가 생성)
├── vector_db/               # 벡터 DB 폴더 (자동 생성, gitignore됨)
└── secure_pdfs/             # PDF 파일 보관 폴더 (선택사항)
```

## 🛠️ 기술 스택

- **Streamlit**: 웹 인터페이스
- **LangChain**: RAG 시스템 구현
- **OpenAI**: 임베딩 및 LLM
- **ChromaDB**: 벡터 데이터베이스
- **PyPDF**: PDF 파일 처리 (변환 시에만 사용)

## 📝 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다.

## 🤝 기여

버그 리포트나 기능 제안은 이슈를 통해 제출해주세요.

---

**참고**: 이 챗봇은 벡터 DB에 저장된 문서 정보를 기반으로 답변합니다. 문서에 없는 내용에 대해서는 "모른다"고 답변할 수 있습니다.
