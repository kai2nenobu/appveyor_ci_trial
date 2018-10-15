
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
