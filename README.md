# 環境構築

以下のコマンドをインストールする

- scoop
- hub
- gibo

参考サイト
[GitHub のコマンドラインツール「hub」の基本と便利な使い方のまとめ | DevelopersIO](https://dev.classmethod.jp/articles/hub/)  
[github/hub: A command-line tool that makes git easier to use with GitHub.](https://github.com/github/hub)  
[ScoopInstaller/Scoop: A command-line installer for Windows.](https://github.com/ScoopInstaller/Scoop)  

```powershell
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
scoop --version
scoop update
scoop install hub
hub --version
scoop install gibo
gibo version
```

PowerShellでhubをgitのエイリアスに設定する

```powershell
Set-Alias git hub
```

## リポジトリ作成

作業フォルダを用意する(フォルダ名は任意、リポジトリ名になる)

```powershell
mkdir project-name
cd project-name
git init

# このプロジェクトの user を設定する
git config user.name ryohei-ochi-fr
git config user.name
git config user.email ryohei.ochi@futurerays.biz
git config user.email
gibo update
gibo dump Node VisualStudioCode > .gitignore

# vscode を起動する
code .
```

github に、リポジトリ(remote)を作成する

```powershell
git create
```

`github.com username` メアドじゃないユーザ名 ryohei-ochi-fr
`github.com password` アクセストークン

```powershell
Error creating repository: Unauthorized (HTTP 401)
Bad credentials
```

認証エラーとなる場合はhubの設定ファイルを確認する

```powershell
type ~/.config/hub
```

エラーになっているけど、リポジトリは作成されているのでとりあえずヨシ

```powershell
github.com username: ryohei.ochi@futurerays.biz
github.com password for ryohei.ochi@futurerays.biz (never stored): 
Updating origin
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
error: Could not fetch origin
```

```powershell
PS > git remote -v
origin  git@github.com:ryohei-ochi-fr/project-name.git (fetch)
origin  git@github.com:ryohei-ochi-fr/project-name.git (push)
```

urlを整える

```powershell
git remote set-url origin https://ryohei-ochi-fr@github.com/ryohei-ochi-fr/project-name.git
```

ブラウザでリモートリポジトリを確認する

```powershell
# hub のコマンド
#hub browse
git browse
```

## first commit

```powershell
git add README.md
git commit -m "first commit"

or

git add .
git commit -m "first commit"

git status
git branch

git branch -m master
git push -u origin master
```

## メモ

```powershell
cd mixnuts
nest new api

cd api
npm init -y
npm install @nestjs/swagger swagger-ui-express --save
npm install typescript ts-node @types/node --save-dev
#npm install prisma --save-dev
#npm install @prisma/client

# 日付処理用
npm install date-fns --save

# xlsx
npm install node-xlsx --save

npm install excel4node --save
npm install sharp --save
npm install buffer-replace --save
[draw.io で作成した SVG で not supported by viewer と表示される。 - へっぽこプログラマーの備忘録](https://kuttsun.blogspot.com/2018/01/drawio-svg-not-supported-by-viewer.html)

[markdown-it - npm](https://www.npmjs.com/package/markdown-it)
npm install markdown-it --save





# 起動確認
#npx prisma

# sqliteを利用する
#npx prisma init --datasource-provider sqlite

# .envにdbファイルを書く

# スキーマを確認する
# The Prisma schema provides an intuitive way to model data. Add the following models to your schema.prisma file:

# モデルを作成する schema.prismaファイル

# マイグレーション
npx prisma migrate dev --name init

# マスタなどの仕込み(Seed the database)
#npx prisma db seed

## PrismaStudio の起動
npx prisma studio

# prismaサービス生成
npx nest generate module prisma
npx nest generate service prisma



# APIのリソースを作成する
nest g resource jobs

## スキーマを変更した場合
npx prisma generate
npx prisma migrate dev --name init


# 実行 ホットリロード
nest start --watch

もしくは
npm run start:dev



# 
npm install ffprobe --save
npm install ffprobe-static -save

```

## 参考情報

[Prisma 基礎](https://zenn.dev/smish0000/articles/f1a6f463417b65)
[Build a REST API with NestJS, Prisma, PostgreSQL and Swagger](https://www.prisma.io/blog/nestjs-prisma-rest-api-7D056s1BmOL0)

```text
# めも
npm install --save-dev @vegardit/prisma-generator-nestjs-dto
npx prisma generate
```
