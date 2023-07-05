# Version
* Ruby version
3.2.2

* Rails
7.0.6

* Database
sqlite3

# Run
1. ターミナルを起動
2. 好みの場所にリポジトリを作成し、移動
    ```
    mkdir なんとかなんとか/new_app
    cd なんとかなんとか/new_app
    git clone
    ```
3. アプリのリポジトリに下記をgit clone
    ```
    https://github.com/morihagi/docker_rails_new_sqlite3.git
    ```
4. Dockerコンテナを作る
    ```
    docker compose up --build
    ```
5. rails new
    ```
    docker compose run web rails new . --force --skip-test --skip-bundle
    ```
6. gemのインストール
    ```
    docker compose run web bundle install --path vendor/bundle
    ```
7. サーバーの再起動
    ```
    docker compose exec web bundle exec rails restart
    ```
8. Dockerコンテナに入り、開発を進める
   ```
   docker compose exec web bash
   ```
   root@なんちゃらかんちゃら:/app#みたいなのが表示されればコンテナに入れてます

   - コンテナ内のコマンド例
      ```
      root@なんちゃらかんちゃら:/app# rails db:create
      ```