<!-- -*- mode: markdown -*- coding: utf-8 -*- -->
# Cowoll at Netlify

## Set Up

create a project

    $ lecktor quickstart

* Project Name: Cowoll at Netlify
* Author: higebobo
* Directory: cowroll.netlify.com

## Github

create repository called "cowroll.netlify.com" by higebobo (not cowroll)<sup id="a1">[1](#f1)</sup>

<b id="f1">1:</b> netlifyがusername(not organization)でしかレポジトリを利用できないから
    
## Deploy

gitのURLはhigeboboかcowrollか注意すること(pluginを使う場合は後者)

    $ echo "*~" >> .gitignore
    $ echo "*.bak" >> .gitignore
    $ echo "*.pyc" >> .gitignore
    $ echo "build" >> .gitignore
    $ mv Coroll\ in\ Netlify.lektorproject website.lektorproject
    $ git init
    $ git add .
    $ git commit -m 'First commit'
    $ git remote add origin git@github.com:higebobo/cowroll.netlify.com.git
    $ git remote -v
    $ git push -u origin master

## Netlify

### by tutorial[^2]

* githubのhigeboboアカウントでログイン
* Siteを作成
    - Site Name: cowroll
    - Conifgure Deploys and Repository
        + Dir: build
        + Build Command: lektor build --output-path ./build
* 結局 lektor comannd not foundになって断念

### lektor-netlify plugin

* [^2]: tutorial がうまくいかなかったので lektor-netlify plugin を使う
* higeboboアカウントでなくてもよくなったのでcowrollに移譲
* または

        $ git remote add origin git@github.com:cowroll/cowroll.netlify.com.git

#### netlify-cliのインストール

    $ npm install netlify-cli -g
    $ ndenv rehash

#### アクセスTOKENの生成

以下にアクセスしてTOKEN生成(App IDではない)

https://app.netlify.com/account/applications/personal

website.lektorproject

    [servers.production]
    name = Production
    target = netlify://cowroll.netlify.com
    key = <ACCESS_TOKEN>

#### デプロイ

deploy

	$ lektor deploy production

or

    $ lektor deploy production --key <ACCESS_TOKEN>
