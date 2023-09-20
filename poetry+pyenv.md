# poetry+pyenv

## install pyenv

```
-- 公式のレポからインストール
$ git clone https://github.com/pyenv/pyenv.git ~/.pyenv

-- コンパイルすることで高速化(仮に失敗しても問題なく動く)
$ cd ~/.pyenv && src/configure && make -C src

```

ただし、Macの場合Homebrewでも入れられる

### 対応可能なpython versionの確認

`pyenv install --list`

## Install poetry

> Mac
>
> > `$ curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -`

> Windows 
>
> > https://qiita.com/kerobot/items/3f4064d5174676080585#poetry-%E3%81%AE%E5%B0%8E%E5%85%A5

## pjt set up

```$ pyenv versions
$ pyenv versions
  system
* 3.7.10 (set by /home/あなたのユーザー名/.pyenv/version)
  3.8.2
```

### pjtを置くdirを作成する

下記例

```
$ cd ~/Documents

-- ディレクトリ名は適当
$ mkdir pp-practice
$ cd pp-practice
```

### Poetry set up

`poetry init`でセットアップを始める。

下記は例

```$ poetry init
This command will guide you through creating your pyproject.toml config.

-- パッケージネームを指定
Package name [pp-practice]:
-- パッケージバージョン
Version [0.1.0]:
-- パッケージ説明
Description []:
-- パッケージAuthor指定
Author [あなたのユーザー名 <hogehogemail@example.com>, n to skip]:
-- ライセンスを指定, MITとか
License []:
-- 対応するPythonバージョン, 今回は3.7以上にしました
Compatible Python versions [^3.8]:  ^3.7

-- 対話的にPJの依存パッケージを入れるか
Would you like to define your main dependencies interactively? (yes/no) [yes] no
-- 対話的にPJの開発用の依存パッケージを入れるか
Would you like to define your development dependencies interactively? (yes/no) [yes] no
Generated file

[tool.poetry]
name = "pp-practice"
version = "0.1.0"
description = ""
authors = ["あなたのユーザー名 <hogehogemail@example.com>"]

[tool.poetry.dependencies]
python = "^3.7"

[tool.poetry.dev-dependencies]

[build-system]
requires = ["poetry-core>=1.0.0"]
build-backend = "poetry.core.masonry.api"

-- 上記設定でPJを作って良いか
Do you confirm generation? (yes/no) [yes] yes
```



結果、`pyproject.toml`が作成される

### poetry で使用する仮想環境の構築

```
$ poetry env use 3.x.x
```

環境内でpyを実行する場合は

```system
poetry run python Hoge.py
```

環境に入りっぱなしにするには

```
$ poetry shell
. /home/あなたのユーザー名/.cache/pypoetry/virtualenvs/pp-practice-vAysUxcS-py3.7/bin/activate
(pp-practice-vAysUxcS-py3.7) $
```

#### poetryによるパッケージ管理

```
poetry add hoge
```

上記だけで依存関係を満たして良い感じにインストールしてくれる

消す場合は

```
poetry remove fuga
```



#### 新しくもらった環境を動かす場合

`git clone`なりして、pyenvを入れたら`poetry install`をすると必要なものが全て入る。

