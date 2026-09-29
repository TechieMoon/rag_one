# 멀티모달(이미지 입력) 사용법

텍스트뿐 아니라 이미지까지 함께 입력으로 받아 답변하는 멀티모달 LLM 호출도 실습했다. OpenAI의 `gpt-4o-mini`는 이미지 URL(또는 로컬 이미지를 base64로 인코딩한 data URL)을 메시지에 넣어 호출할 수 있다.

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(
    temperature=0.1,
    model_name="gpt-4o-mini",
)
```

이미지 경로를 그대로 API에 보낼 수는 없어서, 로컬 파일이면 base64로 인코딩한 `data:` URL로 바꾸고 이미 `http(s)` URL이면 그대로 쓰는 헬퍼 함수를 만들었다.

```python
import base64
from pathlib import Path

def image_url(image_source):
    """로컬 이미지 경로 → base64 data URL로 변환, http(s) URL이면 그대로 사용"""
    if str(image_source).startswith(("http://", "https://")):
        return str(image_source)

    image_path = Path(image_source)
    mime_type = "image/png" if image_path.suffix.lower() == ".png" else "image/jpeg"
    encoded_image = base64.b64encode(image_path.read_bytes()).decode("utf-8")
    return f"data:{mime_type};base64,{encoded_image}"
```

`HumanMessage`의 `content`를 리스트로 주면 텍스트와 이미지를 한 메시지에 같이 담을 수 있다. 이미지는 `{"type": "image_url", "image_url": {"url": ...}}` 형태로 넣는다.

```python
from langchain_core.messages import HumanMessage, SystemMessage

def build_multimodal_messages(image_source, user_prompt=None, system_prompt=None):
    messages = [SystemMessage(content=system_prompt or "You are a helpful assistant on parsing images.")]
    content = [
        {"type": "text", "text": user_prompt or "Explain the given images in-depth."},
        {"type": "image_url", "image_url": {"url": image_url(image_source)}},
    ]
    messages.append(HumanMessage(content=content))
    return messages
```

답변을 스트리밍으로 받아서 토큰 단위로 바로 출력하는 함수도 함께 만들었다.

```python
from langchain_core.messages import AIMessageChunk

def stream_response(response, return_output=False):
    answer = ""
    for token in response:
        content = token.content if isinstance(token, AIMessageChunk) else token
        answer += content
        print(content, end="", flush=True)
    print()
    if return_output:
        return answer
```

이미지 URL을 넘겨서 실제로 호출해보면, 이미지를 화면에 띄우고 모델이 이미지를 설명하는 답변을 스트리밍으로 출력한다.

```python
IMAGE_URL = "https://t3.ftcdn.net/jpg/03/77/33/96/360_F_377339633_Rtv9I77sSmSNcev8bEcnVxTHrXB4nRJ5.jpg"

stream_image_response(IMAGE_URL)
```
