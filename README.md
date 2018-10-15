
# ビルドスクリプトのファイル名

リポジトリルートの `appveyor.yml` か `.appveyor.yml` なら自動で認識してくれる。
それ以外のファイル名にしたい場合はAppVeyorの `Settings > General > Custom configuration .yml file name` を
設定すればよい。

# ビルド実行順

ビルドの各ブロックの実行順は想像通りだけど以下のようになる。

```
install
before_build
build_script
after_build
before_test
test_script
after_test
before_deploy
deploy_script
after_deploy
on_success
on_finish
```

# タグの種類によるビルド環境変数の違い

`master` ブランチのコミット bc7e9554fb4142ed7e54eb58222a85acf59efe10 に対して、軽量タグ `sample-lightweight-tag` とアノテーションタグ `sample-annnotated-tag` をつけてそれぞれビルドした場合を比較してみる。

## 普通のコミット

- https://ci.appveyor.com/project/kai2nenobu/appveyor-ci-trial/builds/19506703

```
APPVEYOR_ACCOUNT_NAME=kai2nenobu
APPVEYOR_API_URL=http://localhost:1038/
APPVEYOR_BUILD_AGENT_HYPERV_NIC_CONFIGURED=true
APPVEYOR_BUILD_FOLDER=C:\projects\appveyor-ci-trial
APPVEYOR_BUILD_ID=19506703
APPVEYOR_BUILD_NUMBER=10
APPVEYOR_BUILD_VERSION=0.0.10
APPVEYOR_BUILD_WORKER_IMAGE=Visual Studio 2015
APPVEYOR_JOB_ID=ibedbuy075kp5oy1
APPVEYOR_JOB_NUMBER=1
APPVEYOR_PROJECT_ID=502741
APPVEYOR_PROJECT_NAME=appveyor_ci_trial
APPVEYOR_PROJECT_SLUG=appveyor-ci-trial
APPVEYOR_REPO_BRANCH=master
APPVEYOR_REPO_COMMIT_AUTHOR_EMAIL=kai2nenobu@gmail.com
APPVEYOR_REPO_COMMIT_AUTHOR=Tsunenobu Kai
APPVEYOR_REPO_COMMIT_MESSAGE_EXTENDED=AppVeyor???????????????????????????????????\n?????????????????\n\n`Commit "4af6bfa0" skipped as branch "sample-annotated-tag" is not in white-list`\n\n?????????????????????????\n???????????????????????????????
APPVEYOR_REPO_COMMIT_MESSAGE=????????????????????????????????
APPVEYOR_REPO_COMMIT_TIMESTAMP=2018-10-15T04:30:17.0000000Z
APPVEYOR_REPO_COMMIT=bc7e9554fb4142ed7e54eb58222a85acf59efe10
APPVEYOR_REPO_NAME=kai2nenobu/appveyor_ci_trial
APPVEYOR_REPO_PROVIDER=gitHub
APPVEYOR_REPO_SCM=git
APPVEYOR_REPO_TAG=false
APPVEYOR_URL=https://ci.appveyor.com
APPVEYOR=True
CI_LINUX=False
CI_WINDOWS=True
CI=True
```

## 軽量タグ

- https://ci.appveyor.com/project/kai2nenobu/appveyor-ci-trial/builds/19506712

```
APPVEYOR_ACCOUNT_NAME=kai2nenobu
APPVEYOR_API_URL=http://localhost:1034/
APPVEYOR_BUILD_AGENT_HYPERV_NIC_CONFIGURED=true
APPVEYOR_BUILD_FOLDER=C:\projects\appveyor-ci-trial
APPVEYOR_BUILD_ID=19506712
APPVEYOR_BUILD_NUMBER=11
APPVEYOR_BUILD_VERSION=0.0.11
APPVEYOR_BUILD_WORKER_IMAGE=Visual Studio 2015
APPVEYOR_JOB_ID=xelxhonk80rikjei
APPVEYOR_JOB_NUMBER=1
APPVEYOR_PROJECT_ID=502741
APPVEYOR_PROJECT_NAME=appveyor_ci_trial
APPVEYOR_PROJECT_SLUG=appveyor-ci-trial
APPVEYOR_REPO_BRANCH=master
APPVEYOR_REPO_COMMIT_AUTHOR_EMAIL=kai2nenobu@gmail.com
APPVEYOR_REPO_COMMIT_AUTHOR=Tsunenobu Kai
APPVEYOR_REPO_COMMIT_MESSAGE_EXTENDED=AppVeyor???????????????????????????????????\n?????????????????\n\n`Commit "4af6bfa0" skipped as branch "sample-annotated-tag" is not in white-list`\n\n?????????????????????????\n???????????????????????????????
APPVEYOR_REPO_COMMIT_MESSAGE=????????????????????????????????
APPVEYOR_REPO_COMMIT_TIMESTAMP=2018-10-15T04:30:17.0000000Z
APPVEYOR_REPO_COMMIT=bc7e9554fb4142ed7e54eb58222a85acf59efe10
APPVEYOR_REPO_NAME=kai2nenobu/appveyor_ci_trial
APPVEYOR_REPO_PROVIDER=gitHub
APPVEYOR_REPO_SCM=git
APPVEYOR_REPO_TAG_NAME=sample-lightweight-tag
APPVEYOR_REPO_TAG=true
APPVEYOR_URL=https://ci.appveyor.com
APPVEYOR=True
CI_LINUX=False
CI_WINDOWS=True
CI=True
```

## アノテーションタグ

- https://ci.appveyor.com/project/kai2nenobu/appveyor-ci-trial/builds/19506722

```
APPVEYOR_ACCOUNT_NAME=kai2nenobu
APPVEYOR_API_URL=http://localhost:1040/
APPVEYOR_BUILD_AGENT_HYPERV_NIC_CONFIGURED=true
APPVEYOR_BUILD_FOLDER=C:\projects\appveyor-ci-trial
APPVEYOR_BUILD_ID=19506722
APPVEYOR_BUILD_NUMBER=12
APPVEYOR_BUILD_VERSION=0.0.12
APPVEYOR_BUILD_WORKER_IMAGE=Visual Studio 2015
APPVEYOR_JOB_ID=if4nhevlg9nec6cw
APPVEYOR_JOB_NUMBER=1
APPVEYOR_PROJECT_ID=502741
APPVEYOR_PROJECT_NAME=appveyor_ci_trial
APPVEYOR_PROJECT_SLUG=appveyor-ci-trial
APPVEYOR_REPO_BRANCH=sample-annotated-tag
APPVEYOR_REPO_COMMIT_AUTHOR_EMAIL=kai2nenobu@gmail.com
APPVEYOR_REPO_COMMIT_AUTHOR=Tsunenobu Kai
APPVEYOR_REPO_COMMIT_MESSAGE_EXTENDED=AppVeyor???????????????????????????????????\n?????????????????\n\n`Commit "4af6bfa0" skipped as branch "sample-annotated-tag" is not in white-list`\n\n?????????????????????????\n???????????????????????????????
APPVEYOR_REPO_COMMIT_MESSAGE=????????????????????????????????
APPVEYOR_REPO_COMMIT_TIMESTAMP=2018-10-15T04:30:17.0000000Z
APPVEYOR_REPO_COMMIT=bc7e9554fb4142ed7e54eb58222a85acf59efe10
APPVEYOR_REPO_NAME=kai2nenobu/appveyor_ci_trial
APPVEYOR_REPO_PROVIDER=gitHub
APPVEYOR_REPO_SCM=git
APPVEYOR_REPO_TAG_NAME=sample-annotated-tag
APPVEYOR_REPO_TAG=true
APPVEYOR_URL=https://ci.appveyor.com
APPVEYOR=True
CI_LINUX=False
CI_WINDOWS=True
CI=True
```

## 比較

| 環境変数               | コミット | 軽量タグ               | アノテーションタグ    |
|------------------------|----------|------------------------|-----------------------|
| APPVEYOR_REPO_BRANCH   | master   | master                 | sample-annnotated-tag |
| APPVEYOR_REPO_TAG      | false    | true                   | true                  |
| APPVEYOR_REPO_TAG_NAME |          | sample-lightweight-tag | sample-annnotated-tag |

- https://www.appveyor.com/docs/branches/#build-on-tags-github-gitlab-and-bitbucket-only

に記載の通り、アノテーションタグは紐づくブランチ名が取得できないので、
ブランチ名がタグ名と同じ値になっているようだ。アノテーションタグでのビルド動作を
変えたい場合に気をつけないといけない。
