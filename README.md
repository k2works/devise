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

6. config/route.rbを編集

7. デフォルトのページをリネーム

8. 認証関連ページを日本語化する

### 参照

[本家](https://github.com/plataformatec/devise)

[deviseによる認証を組み込んだRails3アプリの作成](http://takemikami.com/technote/archives/653)

