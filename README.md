# co6ted.github.io
- 静的サイトジェネレーターであるHugoを使って作成した
- フォルダ構成などのメモを記載していく

## 新規Webサイトを作成する
- 下記コマンドを実行するとフォルダが作成される

```shell
$ hugo new site <好きなフォルダ名>
```

### 作成されたフォルダの構成
- archetypes
  - 記事の雛型を配置するフォルダ
- content
  - 記事を配置するフォルダ
  - markdownファイルを格納する
- data
  - データファイルを配置するフォルダ
- layouts
  - サイトのレイアウトを配置するフォルダ
- public
  - hugoビルド後のデータが格納される
  - config.tomlで好きな出力先を指定することができる
    - 私の場合は「docs」とした
- static
  - JS/CSS/画像等の素材を配置するフォルダ
  - hugoビルド時に加工せずそのまま出力される
- themes
  - 利用したいテーマを配置するフォルダ
  - Hugoのテーマは[このサイト](https://themes.gohugo.io/)で見ることができる
  - テーマを利用する際にはconfig.tomlで指定する
- config.toml
  - サイト全体の設定ファイル

## サイトの確認
- 記事やレイアウトを変更した際に実際に適応されているか確認をしたいと思う
  - その時には下記コマンドを実行することでサーバが立ち上がりローカルで確認することができる

```shell
$ hugo server
```

## ビルド
- 確認が済んだらビルドを行う
- とても簡単でhugoと打つだけで完了する
- config.tomlで出力先を指定していない場合はpublicに静的コンテンツが格納される

```shell
$ hugo
```

## デプロイ(手動)
- 私の場合はGitHub Pagesを利用している
- co6ted.github.ioリポジトリのsourceブランチにビルドしたものも含めて全てpushする
- その後、masterブランチにdocsフォルダをpushすることで対応している

デプロイの方法は下記を参考にした
- https://qiita.com/kwappa/items/03ffdeb89039a7249619

## デプロイ(自動)
- 上記の手動方法でデプロイしていたがGitHub ActionsのWorkflowで自動デプロイできるようにした
- co6ted.github.ioリポジトリのsourceブランチに変更したものをpushのみで良くなった
  - 手動ではビルドをする必要もあったがworkflow処理時にビルドされる
- その後、masterブランチのdocsフォルダにデプロイされて公開完了の流れとなった
