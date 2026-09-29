# 테디노트의 랭체인을 활용한 RAG 비법노트 (기본편) — 최신 코드 복습 노트

## 이 레포지토리는?

[teddylee777/langchain-kr](https://github.com/teddylee777/langchain-kr)에 있는 책 예제 코드는 작성된 지 시간이 지나서, 지금의 LangChain(1.x)에서는 에러가 나거나 더 이상 권장되지 않는(deprecated) API를 쓰는 부분이 많습니다.
이 레포지토리는 책을 공부하면서 **최신 LangChain 방식으로 직접 고쳐서 실행해 본 코드와 정리 문서**를 책 목차 순서대로 모아둔 복습용 저장소입니다.

- 날짜별 학습 기록은 [hanwha_0902](https://github.com/TechieMoon/hanwha_0902)에 있고, 여기는 같은 내용을 **책 챕터 기준**으로 재정리한 것입니다.
- 폴더는 `chXX/`(챕터), 파일은 `절번호_내용.ipynb` 형식입니다. 예) `ch13/05_parent_document_retriever.ipynb` = CHAPTER 13의 05절
- 한 노트북이 여러 절을 다루면 `01-05_...`처럼 범위로 표시했습니다.
- 같은 이름의 `.md` 파일이 그 노트북의 정리 문서입니다.

## 실행 환경

```bash
python -m venv .venv
.venv\Scripts\activate        # Windows
pip install -r requirements.txt
```

루트에 `.env` 파일을 만들고 `.env.example`을 참고해 API 키를 넣어주세요. (`.env`는 `.gitignore`에 포함되어 있어 커밋되지 않습니다.)
노트북은 각 챕터 폴더 안에서 실행하는 것을 기준으로 작성되어 있습니다. (`data/`, `prompts/` 등 상대 경로 사용)

## 목차

코드/문서가 있는 절은 링크가 걸려 있고, `-`는 아직 정리하지 않은 절입니다.

### PART 01 처음 만나는 LangChain


**CHAPTER 01 RAG 이해하기** → [`ch01/`](ch01/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | RAG를 사용해야 하는 이유 | - | - |  |
| 02 | RAG의 기막힌 능력 | - | - |  |
| 03 | LangChain을 이용한 RAG 시스템 구축 | [03_rag_basic_pdf_pipeline.ipynb](ch01/03_rag_basic_pdf_pipeline.ipynb) | [03_rag_basic_pdf_pipeline.md](ch01/03_rag_basic_pdf_pipeline.md) | PDF 로드 → 분할 → 임베딩 → FAISS → 리트리버 → 프롬프트 → LLM → 체인 8단계 |

**CHAPTER 02 환경 설정** → [`ch02/`](ch02/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | 윈도우에서 환경 설치 | - | - |  |
| 02 | MacOS에서 환경 설치 | - | - |  |
| 03 | OpenAI API 키 발급 및 설정하기 | [03_openai_api_key_test.py](ch02/03_openai_api_key_test.py) | [03_openai_api_key_test.md](ch02/03_openai_api_key_test.md) |  |
| 04 | LangSmith 키 발급 및 설정하기 | - | - |  |

**CHAPTER 03 LLM 기본 용어** → [`ch03/`](ch03/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | Jupyter Notebook 사용법 | [01_venv_and_dotenv_check.ipynb](ch03/01_venv_and_dotenv_check.ipynb) | - |  |
| 02 | 토큰, 토큰 계산기, 모델별 토큰 비용 | - | - |  |
| 03 | 모델의 입출력과 컨텍스트 윈도우 | - | - |  |

**CHAPTER 04 LangChain 시작하기** → [`ch04/`](ch04/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | ChatOpenAI 주요 매개변수와 출력 | [01_chatopenai_first_try.ipynb](ch04/01_chatopenai_first_try.ipynb)<br>[01_chatopenai_params_logprobs_streaming.ipynb](ch04/01_chatopenai_params_logprobs_streaming.ipynb)<br>[01_openai_sdk_direct_call.ipynb](ch04/01_openai_sdk_direct_call.ipynb) | [01_chatopenai_params_logprobs_streaming.md](ch04/01_chatopenai_params_logprobs_streaming.md) |  |
| 02 | LangSmith로 GPT 추론 내용 추적하기 | [02_langsmith_tracing_and_agent.ipynb](ch04/02_langsmith_tracing_and_agent.ipynb) | [02_langsmith_tracing_and_agent.md](ch04/02_langsmith_tracing_and_agent.md) |  |
| 03 | 멀티모달 모델로 이미지를 인식하여 답변 출력하기 | [03_multimodal_image_input.ipynb](ch04/03_multimodal_image_input.ipynb) | [03_multimodal_image_input.md](ch04/03_multimodal_image_input.md) |  |
| 04 | 프롬프트 템플릿 활용하기 | - | - |  |
| 05 | LCEL로 체인 생성하기 | - | - |  |
| 06 | 출력 파서를 체인에 연결하기 | - | - |  |
| 07 | batch() 함수로 일괄 처리하기 | - | - |  |
| 08 | 비동기 호출 방법 | - | - |  |
| 09 | Runnable로 병렬 체인 구성하기 | - | - |  |
| 10 | 값을 전달해 주는 RunnablePassthrough | - | - |  |
| 11 | 병렬로 Runnable을 실행하는 RunnableParallel | - | - |  |
| 12 | 함수를 실행하는 RunnableLambda와 itemgetter | - | - |  |

### PART 02 프롬프트와 출력 파서


**CHAPTER 05 프롬프트** → [`ch05/`](ch05/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | 프롬프트 템플릿 만들기 | [01-05_prompt_templates.ipynb](ch05/01-05_prompt_templates.ipynb) | [01-05_prompt_templates.md](ch05/01-05_prompt_templates.md) |  |
| 02 | 부분 변수 활용하기 | [01-05_prompt_templates.ipynb](ch05/01-05_prompt_templates.ipynb) | [01-05_prompt_templates.md](ch05/01-05_prompt_templates.md) |  |
| 03 | YAML 파일로부터 프롬프트 템플릿 로드하기 | [01-05_prompt_templates.ipynb](ch05/01-05_prompt_templates.ipynb) | [01-05_prompt_templates.md](ch05/01-05_prompt_templates.md) |  |
| 04 | ChatPromptTemplate | [01-05_prompt_templates.ipynb](ch05/01-05_prompt_templates.ipynb) | [01-05_prompt_templates.md](ch05/01-05_prompt_templates.md) |  |
| 05 | MessagesPlaceholder | [01-05_prompt_templates.ipynb](ch05/01-05_prompt_templates.ipynb) | [01-05_prompt_templates.md](ch05/01-05_prompt_templates.md) |  |
| 06 | 퓨샷 프롬프트 | [06_few_shot_prompt.ipynb](ch05/06_few_shot_prompt.ipynb) | [06_few_shot_prompt.md](ch05/06_few_shot_prompt.md) |  |
| 07 | 예제 선택기 | - | - |  |
| 08 | FewShotChatMessagePromptTemplate | - | - |  |
| 09 | 목적에 맞는 예제 선택기 | - | - |  |
| 10 | LangChain Hub에서 프롬프트 공유하기 | - | - |  |

**CHAPTER 06 출력 파서** → [`ch06/`](ch06/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | PydanticOutputParser | [01-02_pydantic_output_parser.ipynb](ch06/01-02_pydantic_output_parser.ipynb) | [01-02_pydantic_output_parser.md](ch06/01-02_pydantic_output_parser.md) |  |
| 02 | with_structured_output() 바인딩 | [01-02_pydantic_output_parser.ipynb](ch06/01-02_pydantic_output_parser.ipynb) | [01-02_pydantic_output_parser.md](ch06/01-02_pydantic_output_parser.md) |  |
| 03 | LangSmith에서 출력 파서의 흐름 확인하기 | - | - |  |
| 04 | 쉼표로 구분된 리스트 출력 파서 | [04_comma_separated_list_parser.ipynb](ch06/04_comma_separated_list_parser.ipynb) | [04_comma_separated_list_parser.md](ch06/04_comma_separated_list_parser.md) |  |
| 05 | 구조화된 출력 파서 | [05_structured_output_answer_with_source.ipynb](ch06/05_structured_output_answer_with_source.ipynb) | [05_structured_output_answer_with_source.md](ch06/05_structured_output_answer_with_source.md) | 책의 `StructuredOutputParser`/`ResponseSchema` 대신 `with_structured_output()`으로 답변+출처 받기 |
| 06 | JSON 형식 출력 파서 | - | - |  |
| 07 | Pandas 데이터프레임 출력 파서 | - | - |  |
| 08 | 날짜 형식 출력 파서 | - | - |  |
| 09 | 열거형 출력 파서 | - | - |  |

### PART 03 모델과 메모리


**CHAPTER 07 모델** → [`ch07/`](ch07/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | RAG에서 LLM의 역할과 모델의 종류 | - | - |  |
| 02 | 다양한 LLM 활용 방법과 API 키 가져오기 | - | - |  |
| 03 | LLM 답변 캐싱하기 | [03_llm_cache_inmemory_sqlite.ipynb](ch07/03_llm_cache_inmemory_sqlite.ipynb) | [03_llm_cache_inmemory_sqlite.md](ch07/03_llm_cache_inmemory_sqlite.md) |  |
| 04 | 직렬화와 역직렬화로 모델 저장 및 로드하기 | [04_chain_serialization.ipynb](ch07/04_chain_serialization.ipynb) | [04_chain_serialization.md](ch07/04_chain_serialization.md) |  |
| 05 | GPT 모델의 토큰 사용량 확인하기 | [05_token_usage_callback.ipynb](ch07/05_token_usage_callback.ipynb) | [05_token_usage_callback.md](ch07/05_token_usage_callback.md) | `get_openai_callback` 대신 `get_usage_metadata_callback` 사용 |
| 06 | Google Generative AI 모델 | [06_google_gemini.ipynb](ch07/06_google_gemini.ipynb) | [06_google_gemini.md](ch07/06_google_gemini.md) |  |
| 07 | Hugging Face Inference API 활용하기 | - | - |  |
| 08 | Dedicated Inference Endpoint로 원격 호스팅하기 | - | - |  |
| 09 | Hugging Face 로컬 모델 다운로드 받아 추론하기 | - | - |  |
| 10 | Ollama 설치 및 Modelfile 설정하기 | - | - |  |
| 11 | Ollama 모델 생성하고 ChatOllama 활용하기 | - | - |  |
| 12 | GPT4All로 로컬 모델 실행하기 | - | - |  |

**CHAPTER 08 메모리** → [`ch08/`](ch08/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | 대화 버퍼 메모리 | [01_conversation_memory_with_message_history.ipynb](ch08/01_conversation_memory_with_message_history.ipynb) | [01_conversation_memory_with_message_history.md](ch08/01_conversation_memory_with_message_history.md) | deprecated된 `ConversationBufferMemory`/`ConversationChain` 대신 `InMemoryChatMessageHistory` + `RunnableWithMessageHistory` |
| 02 | 대화 버퍼 윈도우 메모리 | - | - |  |
| 03 | 대화 토큰 버퍼 메모리 | - | - |  |
| 04 | 대화 엔티티 메모리 | - | - |  |
| 05 | 대화 지식 그래프 메모리 | - | - |  |
| 06 | 대화 요약 메모리 | - | - |  |
| 07 | 벡터 스토어 검색 메모리 | - | - |  |
| 08 | LCEL 체인에 메모리 추가하기 | - | - |  |
| 09 | SQLite에 대화 내용 저장하기 | - | - |  |
| 10 | 휘발성 메모리로 일반 변수에 대화 내용 저장하기 | - | - |  |

### PART 04 데이터 로드와 텍스트 분할


**CHAPTER 09 문서 로더** → [`ch09/`](ch09/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | 문서 로더의 구조 이해하기 | [01-02_document_structure_and_pdf_loader.ipynb](ch09/01-02_document_structure_and_pdf_loader.ipynb) | [01-02_document_structure_and_pdf_loader.md](ch09/01-02_document_structure_and_pdf_loader.md) |  |
| 02 | PDF 로더 | [01-02_document_structure_and_pdf_loader.ipynb](ch09/01-02_document_structure_and_pdf_loader.ipynb) | [01-02_document_structure_and_pdf_loader.md](ch09/01-02_document_structure_and_pdf_loader.md) | `PyPDFLoader` + `PyMuPDF4LLMLoader` 비교 |
| 03 | HWP 로더 | - | - |  |
| 04 | CSV 로더와 데이터프레임 로더 | - | - |  |
| 05 | WebBaseLoader | [05_web_base_loader.ipynb](ch09/05_web_base_loader.ipynb) | [05_web_base_loader.md](ch09/05_web_base_loader.md) |  |
| 06 | DirectoryLoader | - | - |  |
| 07 | UpstageDocumentParseLoader | - | - |  |
| 08 | LlamaParse | - | - |  |

**CHAPTER 10 텍스트 분할** → [`ch10/`](ch10/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | 문자 단위로 분할하기 | [01_character_text_splitter.ipynb](ch10/01_character_text_splitter.ipynb) | [01_character_text_splitter.md](ch10/01_character_text_splitter.md) |  |
| 02 | 문자 단위로 재귀적으로 분할하기 | [02_recursive_character_text_splitter.ipynb](ch10/02_recursive_character_text_splitter.ipynb) | [02_recursive_character_text_splitter.md](ch10/02_recursive_character_text_splitter.md) |  |
| 03 | 토큰 단위로 분할하기 | [03_token_and_sentence_text_splitter.ipynb](ch10/03_token_and_sentence_text_splitter.ipynb) | [03_token_and_sentence_text_splitter.md](ch10/03_token_and_sentence_text_splitter.md) |  |
| 04 | 의미 단위로 분할하기 | - | - |  |
| 05 | 코드 분할하기 | - | - |  |
| 06 | 마크다운 헤더로 분할하기 | - | - |  |
| 07 | HTML 헤더로 분할하기 | [07_html_header_text_splitter.ipynb](ch10/07_html_header_text_splitter.ipynb) | [07_html_header_text_splitter.md](ch10/07_html_header_text_splitter.md) |  |
| 08 | JSON 단위로 분할하기 | - | - |  |

### PART 05 벡터 스토어와 리트리버


**CHAPTER 11 임베딩** → [`ch11/`](ch11/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | OpenAIEmbeddings | [01_openai_embeddings.ipynb](ch11/01_openai_embeddings.ipynb) | [01_openai_embeddings.md](ch11/01_openai_embeddings.md) |  |
| 02 | CacheBackedEmbeddings | - | - |  |
| 03 | HuggingFaceEmbeddings | [03_huggingface_embeddings.ipynb](ch11/03_huggingface_embeddings.ipynb) | [03_huggingface_embeddings.md](ch11/03_huggingface_embeddings.md) |  |
| 04 | UpstageEmbeddings | - | - |  |
| 05 | OllamaEmbeddings | - | - |  |

**CHAPTER 12 벡터 스토어** → [`ch12/`](ch12/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | Chroma | [01_chroma_vectorstore.ipynb](ch12/01_chroma_vectorstore.ipynb) | [01_chroma_vectorstore.md](ch12/01_chroma_vectorstore.md) | 멀티모달 검색에서 `langchain_teddynote`의 `MultiModal` 대신 직접 만든 `SimpleMultiModal` 사용 |
| 02 | FAISS | [02_faiss_vectorstore.ipynb](ch12/02_faiss_vectorstore.ipynb) | [02_faiss_vectorstore.md](ch12/02_faiss_vectorstore.md) |  |
| 03 | Pinecone | [03_pinecone_quickstart.ipynb](ch12/03_pinecone_quickstart.ipynb) | - |  |

**CHAPTER 13 리트리버** → [`ch13/`](ch13/)

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | 벡터 스토어 기반 리트리버 | [01_vectorstore_retriever.ipynb](ch13/01_vectorstore_retriever.ipynb) | [01_vectorstore_retriever.md](ch13/01_vectorstore_retriever.md) |  |
| 02 | 문서 압축기 | [02_contextual_compression_retriever.ipynb](ch13/02_contextual_compression_retriever.ipynb) | [02_contextual_compression_retriever.md](ch13/02_contextual_compression_retriever.md) | `langchain.retrievers` → `langchain_classic.retrievers` |
| 03 | 양방향 리트리버 | [03_ensemble_retriever_bm25_faiss.ipynb](ch13/03_ensemble_retriever_bm25_faiss.ipynb) | [03_ensemble_retriever_bm25_faiss.md](ch13/03_ensemble_retriever_bm25_faiss.md) | `langchain_classic.retrievers`의 `BM25Retriever`, `EnsembleRetriever` |
| 04 | 긴 문맥 재정렬 | - | - |  |
| 05 | 부모 문서 리트리버 | [05_parent_document_retriever.ipynb](ch13/05_parent_document_retriever.ipynb) | [05_parent_document_retriever.md](ch13/05_parent_document_retriever.md) | `langchain_classic.retrievers.ParentDocumentRetriever` |
| 06 | 다중 쿼리 생성 리트리버 | - | - |  |
| 07 | 다중 벡터 스토어 리트리버 | - | - |  |
| 08 | 셀프 쿼리 리트리버 | - | - |  |
| 09 | 시간 가중 벡터 스토어 리트리버 | - | - |  |

### PART 06 LangChain 실습


**CHAPTER 14 Streamlit으로 ChatGPT 웹 앱 제작하기**

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | 기본적인 웹 앱 형태 만들기 | - | - |  |
| 02 | 웹 앱에 체인 생성하기 | - | - |  |
| 03 | 프롬프트 타입 선택 기능 추가하기 | - | - |  |

**CHAPTER 15 이메일 업무 자동화 챗봇**

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | 이메일 내용으로부터 구조화된 정보 추출하기 | - | - |  |
| 02 | SerpAPI를 정보 검색에 활용하기 | - | - |  |
| 03 | 구조화된 답변을 다음 체인의 입력으로 추가하기 | - | - |  |
| 04 | 이메일의 주요 정보 및 검색 정보 기반 요약 보고서 챗봇 | - | - |  |

**CHAPTER 16 다양한 모델을 활용한 챗봇**

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | 별도의 파이썬 파일로 기능 분리하기 | - | - |  |
| 02 | GPT 대신 Deepseek 모델 사용하기 | - | - |  |
| 03 | Ollama 모델을 사용한 RAG | - | - |  |
| 04 | 멀티모달 모델을 활용한 이미지 인식 기반 챗봇 | - | - |  |

**CHAPTER 17 RAG 챗봇**

| 절 | 내용 | 코드 | 정리 문서 | 비고 |
|---|---|---|---|---|
| 01 | PDF 문서 기반 질의응답 RAG 만들기 | - | - |  |
| 02 | 프롬프트를 개선해 주는 프롬프트 메이커 | - | - |  |
| 03 | 페이지 분할 후 파일 업로드 기능 추가하기 | - | - |  |
| 04 | PDF 기반 QA 챗봇 만들기 | - | - |  |
| 05 | LangSmith 추적, 다양한 LLM을 RAG에 적용하기 | - | - |  |
| 06 | 프롬프트에 출처 표시하고 표 기능 추가하기 | - | - |  |
