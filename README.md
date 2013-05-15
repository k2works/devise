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

  app/views/home/index.html.erbを編集

        <% if user_signed_in? %>
          <%= link_to "ログアウト", destroy_user_session_path, :method => 'delete' %>
          <%= link_to "ユーザ情報の編集", edit_user_registration_path %>
        <% else %>
          <%= link_to "ログイン", new_user_session_path %>
          <%= link_to "登録", new_user_registration_path %>
        <% end %>

6. config/route.rbを編集

7. デフォルトのページをリネーム

8. 認証関連ページを日本語化する

### 参照

[本家](https://github.com/plataformatec/devise)

[deviseによる認証を組み込んだRails3アプリの作成](http://takemikami.com/technote/archives/653)

