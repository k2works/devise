## Devise認証をRails3に組み込む
### 目的
Railsアプリでユーザー認証機能を簡単に組み込めるようにする。

### 前提条件
* Rails3.2.13
* Ruby-1.9.2p392
* devise(2.2.4)

### 手順
1. Gemfileにdeviseのgemを追記

2. bundle install, devise:installしてdeviseをインストール

   `$ bundle`

   `$ rails g devise:install`

   `$ rails g devise:vies`

   `$ rails g devise user`

   `$ rake db:migrate`

3. config/environments/development.rbを編集

   `config.action_mailer.default_url_options = { :host => 'localhost:3000' }`
   
4. app/views/layouts/application.html.erbを編集

        <body>
          <p class="notice"><%= notice %></p>
          <p class="alert"><%= alert %></p>
        <%= yield %>
        </body>
    
5. ログインページを作成

`$ rails g controller home index`


6. config/route.rbを編集

`root :to => "home#index"`

7. デフォルトのページをリネーム

`$ mv public/index.html public/index.html.bak`

8. 認証関連ページを日本語化する

日本語ファイルをダウンロードする

https://gist.github.com/kawamoto/4729292

config/locales/dvise.ja.ymlとして保存する

config/application.rbを編集する

`config.i18n.default_locale = :ja`

### 参照

[本家](https://github.com/plataformatec/devise)

[deviseによる認証を組み込んだRails3アプリの作成](http://takemikami.com/technote/archives/653)

