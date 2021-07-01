# mac에 python3.x 설치하기


> strongly recommend pyenv! 
> https://github.com/pyenv/pyenv

pyenv는 python 버전 관리를 매우 편리하게 해주는 프로그램이다. MacOS Catalina (v10.15.7) 기준으로, python2.7가 default로 설치되어 있다. 여기에 python 3.x 버전을 설치하고, 이를 기본 python 명령어로 사용하는 것을 매우 번거로운 일이다. pyenv를 이러한 번거로움을 한번에 해결해준다. 뿐만 아니라, 프로젝트 별로 다른 python version을 셋팅해주기도 한다.


1. ```brew update```
2. ```brew install pyenv```
3. ```echo 'eval "$(pyenv init --path)"' >> ~/.zshrc # For Zsh MacOS, if Pyenv is installed with Homebrew: ```
4. ```pyenv install 3.6.9```
5. ```pyenv global 3.6.9 # 이렇게 하면 python3 이 기본 버전으로 변경된다.```
6. ```pip -V # pip version 확인.```


<br><br>
Tip) virtual environment 를 만들고 싶으면 아래 명령어 사용

```
python -m venv .venv
```