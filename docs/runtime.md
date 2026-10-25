# 공통 실습 환경 준비하기

이 문서에서는 각 주차를 진행하기 전 세팅법을 안내합니다.    
주차별로 별도 처리가 필요한 경우에는 주차 README 에 추가하겠습니다.  
이 문서는 로컬과 Colab Web을 기준으로 환경 설정과 코드를 제공합니다.
로컬 실행을 기본으로 사용하고, 자원이 부족하거나 설치가 어려우면 Colab Web을 선택해주세요.

### 로컬

[uv를 설치](https://docs.astral.sh/uv/getting-started/installation/)한 뒤 미션 폴더 루트에서 실행해주세요.

```bash
uv sync --locked
uv run jupyter notebook
```

진행할 주차의 노트북을 열고, uv로 준비한 프로젝트 Python 환경의 **Python 커널**을 선택해주세요.
Python 커널은 노트북의 Python 코드를 실행하는 프로세스입니다. 커널 선택은 어떤 Python 환경과 설치된 패키지로 셀을 실행할지 정하는 설정입니다.

VS Code에서는 노트북 오른쪽 위의 **Select Kernel**을 누른 뒤 **Python Environments**에서 프로젝트 환경을 고릅니다.
최근 사용한 커널 목록만 보이면 **Select Another Kernel**을 선택해 환경 목록을 열어주세요.
자세한 설정은 [VS Code의 Python 커널 선택](https://code.visualstudio.com/docs/datascience/jupyter-kernel-management#python-environments), [VS Code의 노트북 사용법](https://code.visualstudio.com/docs/datascience/jupyter-notebooks), [uv와 Jupyter, VS Code 연결](https://docs.astral.sh/uv/guides/integration/jupyter/#using-jupyter-from-vs-code)을 참고해주세요.

현재 환경 파일의 기준은 Python 3.12, TensorFlow 2.21.0입니다. macOS Intel은 이 TensorFlow 조합을 지원하지 않으므로 원격 대안을 사용해주세요. [TensorFlow 지원 조합](https://www.tensorflow.org/install/pip)

### 패키지 추가

현재 실습에 필요한 패키지는 `pyproject.toml`과 `uv.lock`에 등록해두었습니다.
별도로 사용할 패키지가 있다면 미션 폴더 루트의 로컬 터미널에서 `uv add`로 추가해주세요. 예를 들어 pandas를 추가하려면 다음과 같이 실행합니다.

```bash
uv add pandas
```

`uv add`는 프로젝트의 패키지 설정과 lock, 설치 환경을 함께 갱신합니다. 제거할 때는 `uv remove pandas`를 사용합니다.
변경한 `pyproject.toml`과 `uv.lock`도 코드와 함께 GitHub 레포에 보관해주세요. [uv 패키지 관리 안내](https://docs.astral.sh/uv/concepts/projects/dependencies/#adding-dependencies)

### Colab Web

진행할 주차 노트북을 열고 필요한 입력 파일을 **Google Drive 또는 Colab 런타임**에 업로드해주세요.
입력 파일을 읽거나 결과를 저장할 구체적인 위치는 필요한 경우 해당 주차의 코드에 명시합니다.

Colab에서도 uv로 `pyproject.toml`의 패키지를 설치할 수 있습니다. 미션 폴더 루트의 `pyproject.toml`을 Colab에 준비하고, 노트북의 Web 설치 셀에서 필요한 줄만 주석 해제해주세요. 업로드 예시는 `/content/pyproject.toml`을 읽도록 작성했습니다. Drive의 파일을 사용한다면 마운트한 뒤 설치 경로를 맞춥니다.

```python
import sys
assert sys.version_info[:2] == (3, 12), "Python 3.12 런타임을 선택해주세요."
%pip install uv
!uv pip install --python {sys.executable} -r /content/pyproject.toml
```

`--python {sys.executable}`은 현재 노트북의 Python 커널에 패키지를 설치하도록 지정합니다. 설치 후 Python 커널을 재시작하고 import 셀부터 실행해주세요. [uv의 pyproject 설치](https://docs.astral.sh/uv/pip/packages/#installing-packages-from-files), [설치할 Python 환경 지정](https://docs.astral.sh/uv/pip/environments/#using-arbitrary-python-environments)

로컬의 `uv sync --locked`는 `uv.lock`을 사용하지만, 위 Colab 설치는 `pyproject.toml`에 적힌 패키지 조건을 사용합니다. 현재 주요 패키지 버전은 고정해두었으나, 간접 의존성과 Colab에 미리 설치된 패키지 구성까지 로컬과 같아지는 것은 아닙니다.

Colab에서 uv를 사용하는 예시는 [LLMs-from-scratch의 Python Setup Tips](https://github.com/rasbt/LLMs-from-scratch/blob/main/setup/01_optional-python-setup-preferences/README.md) 첫 부분을 참고할 수 있습니다. 이 자료의 설치 파일 구성은 문서와 다르므로 실습에서는 위 설정 셀을 기준으로 진행해주세요.

### 저장과 복원

| 보관할 내용 | 보관 위치 |
|---|---|
| 작성한 코드와 완성한 노트북 | GitHub 레포 |
| 패키지 설정 `pyproject.toml`, `uv.lock` | 코드와 같은 GitHub 레포 |
| 전처리 결과, 모델 가중치, 학습 기록 등 실행 결과물 | Google Drive 또는 Colab 런타임 |

용량이 큰 가중치, 전처리 결과, 모델 결과물은 Drive 또는 Colab에 보관해주세요. 필요한 경우 저장과 복원 위치는 해당 주차 코드에 명시합니다.
로컬 실습의 결과는 프로젝트 루트의 `artifacts/` 아래에 주차별로 저장합니다. 예를 들어 1주차 JSON은 `artifacts/week1/week1_state.json`에 생성됩니다.
프로젝트 루트나 주차 폴더에서 실행해도 같은 위치에 저장하도록 노트북에서 경로를 설정합니다. Colab Web의 기본 작업 폴더에서는 `/content/artifacts/`를 사용하고, Drive에 직접 저장하려면 코드의 저장 경로를 바꿔주세요.
공유하거나 다시 사용할 파일은 Drive 등에 옮겨 보관합니다.
Colab 런타임의 파일은 VM 삭제 시 사라질 수 있으므로 계속 사용할 결과는 Drive에 보관해주세요. Drive를 마운트한 뒤 실제 저장 코드도 실행해야 합니다.

새 Python 커널에서는 import, 입력 복원, 모델 복원 셀을 순서대로 실행합니다. 필요한 셀은 해당 노트북에 표시합니다.

완료한 모델의 추론 복원과 중단된 학습의 재개는 별도 작업입니다.
최소 검증 손실의 모델 파일은 마지막 학습 epoch까지 자동 재개하는 백업과 다릅니다.
중단에 대비할 학습 백업도 실행 도중 Drive 등 런타임 밖에 저장합니다.

### 연결이 끊겼을 때

Colab Web에서는 런타임 상태와 셀 출력을 확인해주세요.

문제가 계속되면 오류 메시지와 로그, 실행한 명령이나 셀을 기록해주세요.
새 런타임이 필요하면 환경을 준비하고 보관한 파일을 전달한 뒤, 노트북의 복원 셀을 실행합니다.

[Colab FAQ](https://research.google.com/colaboratory/faq.html)

### 다른 도구가 궁금하다면

터미널이나 AI 에이전트로 Colab을 활용해보고 싶다면 [Colab CLI](https://github.com/googlecolab/google-colab-cli)와 [Colab MCP](https://github.com/googlecolab/colab-mcp)의 공식 안내를 참고해보세요.
관심 있는 분이 선택해서 사용해볼 수 있습니다.
