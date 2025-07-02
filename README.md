# 배포용 코드 (Exportable Code)

이 압축 파일은 학습된 모델을 활용하여 추론(inference) 결과를 시각화할 수 있는 간단한 데모를 포함합니다.

## 압축 파일 구조

- `README.md`
- `LICENSE`
- model
  - `model.xml`
  - `model.bin`
  - `config.json`
- python
  - demo_package
    - `__init__.py`
    - executors
      - `__init__.py`
      - `asynchronous.py`
      - `synchronous.py`
    - inference
      - `__init__.py`
      - `inference.py`
    - streamer
      - `__init__.py`
      - `streamer.py`
    - visualizers
      - `__init__.py`
      - `visualizer.py`
      - `vis_utils.py`
  - `demo.py`
  - `requirements.txt`
  - `setup.py`

## 사전 준비 사항

- [Python 3.10](https://www.python.org/downloads/)
- [Git](https://git-scm.com/)

## 데모 실행을 위한 설치 과정

1. pip 설치 (Ubuntu 예시):

sudo apt install python3-pip


2. 가상환경 생성 및 활성화 (예: virtualenv 사용):

python -m pip install virtualenv
python -m virtualenv <가상환경_디렉토리>
source <가상환경_디렉토리>/bin/activate # Windows는 .<...>\Scripts\activate


3. 필수 패키지 설치:

python -m pip install wheel


4. 데모 패키지 설치:

cd python
python setup.py install


## 사용법

1. 도움말 확인:

python3 demo.py -h


2. 추론 실행 예시 (비디오 파일 입력):

python3 demo.py -i <비디오_경로>/inputVideo.mp4


- `Q` 키를 누르면 종료
- 단일 이미지의 경우 빠르게 종료되며, 지속 시각화를 원할 경우 `--loop` 옵션 사용

3. 추론 결과 저장 예시:

python3 demo.py --input <이미지_경로>/input.jpg --models ../model --output 결과저장폴더


⚠ `--loop`와 `--output`은 함께 사용하지 말 것

4. 웹캠으로 실행하기:

sudo apt-get install v4l-utils
v4l2-ctl --list-devices


예시 출력:

Integrated Camera (usb-...):
/dev/video0


→ `/dev/video0`를 `--input` 값으로 사용

## 문제 해결 (Troubleshooting)

1. 프록시 환경에서 pip 사용:

python -m pip install --proxy http://<아이디>:<비밀번호>@<프록시서버>:<포트번호> <패키지명>


2. Anaconda 환경은 OpenVINO가 Python 3.6/3.7에서만 제한적으로 지원되므로, `venv` 또는 `virtualenv` 사용 권장

3. pip 문제 해결:

python -m pip install --upgrade pip
