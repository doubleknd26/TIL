mac에 python3.x 설치하기



pyenv: strongly recommend
https://github.com/pyenv/pyenv


1. brew update


# https://github.com/pyenv/pyenv
2. brew install pyenv


3. echo 'eval "$(pyenv init --path)"' >> ~/.zshrc


4. pyenv install 3.6.9

5. pyenv global 3.6.9


python -m venv .venv

5 pip -V
pip 18.1 from /Users/doubleknd26/IdeaProjects/coupang/galaxy/search/cloud/virtualenv/lib/python3.6/site-packages/pip (python 3.6)


5. pip install -r requirements.txt