# 실습 환경 준비하기

### 로컬

[uv를 설치](https://docs.astral.sh/uv/getting-started/installation/) 한 뒤 미션 폴더 루트에서 실행해주세요.

```bash
# uv.lock에 고정된 패키지를 프로젝트 가상환경에 설치
uv sync --locked
# 프로젝트 가상환경에서 Jupyter Notebook 실행
uv run jupyter notebook
```

프로젝트 `.venv` 커널로 `week1/week1_mission.ipynb`를 열어주세요.  
기준은 Python 3.12·TensorFlow 2.21.0 이며 첫 주는 CPU를 사용합니다.  
macOS Intel은 이 TensorFlow 조합을 지원하지 않으므로 원격 대안을 사용해주세요. [지원 조합](https://www.tensorflow.org/install/pip)

환경은 `pyproject.toml`·`uv.lock`으로 관리하고 `requirements.txt`는 lock에서 생성합니다.  
의존성이 바뀌고 `requirements.txt` 가 필요한 경우, 다음 명령으로 다시 생성합니다.

```bash
# uv.lock의 패키지 목록을 requirements.txt로 저장
uv export --locked --no-emit-project --no-header --format requirements.txt --output-file requirements.txt
```

### Colab CLI

Linux/macOS에서 로컬 노트북을 원격 커널에 실행할 수 있습니다. 아래는 **로컬 터미널** 명령입니다. 먼저 원격 Python이 3.12인지 확인해주세요.

```bash
# 로컬에 Colab CLI 설치
uv tool install google-colab-cli
# 설치된 CLI 버전 확인
colab version
# gdg-week1 이름으로 원격 런타임 생성
colab --auth oauth2 new -s gdg-week1
# 원격 런타임의 Python 버전 출력
printf 'import sys; print(sys.version)\n' | colab --auth oauth2 exec -s gdg-week1
# requirements.txt의 패키지를 원격 런타임에 설치
colab --auth oauth2 install -s gdg-week1 -r requirements.txt
# 실습 노트북을 원격 런타임에서 실행
colab --auth oauth2 exec -s gdg-week1 --timeout 600 -f week1/week1_mission.ipynb
# 세션 실행 기록을 로컬 노트북 파일로 저장
colab --auth oauth2 log -s gdg-week1 -o week1/week1_execution.ipynb
```

첫 인증은 표시되는 안내를 따라주세요.  
실제 버전의 옵션은 [공식 CLI 안내](https://github.com/googlecolab/google-colab-cli) 를 참조해주세요.

완료 후 노트북이 출력한 저장 경로의 JSON을 로컬에 회수합니다.  
아래 원격 경로는 기본 작업 경로 `/content`를 기준으로 한 예시입니다.

```bash
# 결과물을 받을 로컬 폴더 생성
mkdir -p artifacts/week1
# 원격에서 저장한 전처리 상태 JSON을 로컬로 다운로드
colab --auth oauth2 download -s gdg-week1 /content/artifacts/week1/week1_state.json artifacts/week1/week1_state.json
# 원격 런타임 종료 및 자원 반납
colab --auth oauth2 stop -s gdg-week1
```

### 웹 Colab

노트북을 웹 Colab에서 열고 `requirements.txt`를 업로드해주세요.  
노트북 맨 앞의 웹 설치 셀은 기본 주석 상태입니다.  
Python 3.12를 확인한 다음, 필요한 줄만 해제해주세요.  
설치 후 재시작이 안내되면 커널을 재시작합니다.

Drive에 보관하려면 마운트 셀과 `SAVE_DIR`의 Drive 경로를 활성화해주세요.  
완성한 노트북과 `week1_state.json`을 함께 보관합니다.

### 연결이 끊겼을 때

연결이 끊기거나 오류가 나면 실행 상태와 로그를 확인하고 재연결을 시도해주세요.
CLI에서는 `sessions`, `status`, `log`를, 웹에서는 런타임 상태와 셀 출력을 확인해보세요.

문제가 계속되면 오류 메시지와 로그, 실행한 명령이나 셀을 기록해주세요. 이 기록을 바탕으로 원인을 찾아보거나 도움을 요청해주세요.

[Colab FAQ](https://research.google.com/colaboratory/faq.html), [CLI 세션 관리](https://github.com/googlecolab/google-colab-cli/blob/main/docs/01_session_management.md)
