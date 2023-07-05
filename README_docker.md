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
    ```
3. アプリのリポジトリに下記をgit clone
    ```
    git clone https://github.com/morihagi/docker_rails_new_sqlite3.git
    ```
4. Dockerコンテナを作る
    ```
    docker compose build
    ```
5. メインのコンテナを起動
    ```
    docker compose up -d
    ```
    起動はするけど、Railsアプリがないため、すぐに止まります。それでOK。
6. rails new
    ```
    docker compose run web rails new . --force --skip-test --skip-bundle
    ```
    ここでメイン以外のコンテナが起動しますが、無視します。メインのコンテナの中で開発に入れたら削除してOK。
7. gemのインストール
    ```
    docker compose run web bundle install --path vendor/bundle
    ```
    ここでメイン以外のコンテナが起動しますが、無視します。メインのコンテナの中で開発に入れたら削除してOK。
8. メインのコンテナを起動
    ```
    docker compose up -d
    ```
9. Dockerコンテナに入り、開発を進める
    ```
    docker compose exec web bash
    ```
    root@なんちゃらかんちゃら:/app#みたいなのが表示されればコンテナに入れてます

10. その他

    - コンテナ内のコマンド例
        ```
        root@なんちゃらかんちゃら:/app# rails db:create
        ```
    - gemをインストールして、サーバーを再起動したい時
        ```
        # コンテナの外から実行
        docker compose exec web bundle exec rails restart
        ```
    - 全コンテナの停止
        ```
        docker stop $(docker ps -q)
        ```
        `docker compose up -d`で再起動
    - コンテナの削除
        ```
        docker compose down
        ```
        `docker compose up -d`で復活
