# mac에 python3.x 설치하기


> pyenv: strongly recommend
> https://github.com/pyenv/pyenv


1. brew update

2. brew install pyenv

3. ```echo 'eval "$(pyenv init --path)"' >> ~/.zshrc```

4. pyenv install 3.6.9

5. pyenv global 3.6.9 # 이렇게 하면 python3 이 기본 버전으로 변경된다.

6. pip -V # pip version 확인.


tip) virtual environment 를 만들고 싶으면 아래 명령어 사용.

```
python -m venv .venv
```
