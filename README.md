参考  
[https://www.youtube.com/watch?v=ltDdZAJli8c&t=0s]

**contents**

- [ビルド image構築](#ビルド-image構築)
- [コンテナ構築、コンテナ起動](#コンテナ構築コンテナ起動)
- [ブラウザでアクセス](#ブラウザでアクセス)
- [結果](#結果)
- [Q\&A](#qa)
  - [docker-compose downしたほうがいい？](#docker-compose-downしたほうがいい)

## ビルド image構築

```bash
docker-compose build
```

## コンテナ構築、コンテナ起動

```bash
docker-compose up
```

## ブラウザでアクセス

http://localhost:3000/

## 結果

Yay! You’re on Rails!

## Q&A

### docker-compose downしたほうがいい？
 
docker-compose up した後に、 Ctrl+C で止めるけど
docker-compose downしたほうがいい？

`docker-compose up`でコンテナを起動した後、`Ctrl+C`でそれらを停止することは可能です。ただし、これによりコンテナは停止しますが、ネットワーク、ボリューム、イメージなどが削除されません。ですので、再度`docker-compose up`を実行すると、これらのリソースが再利用されます。

一方、`docker-compose down`コマンドは、`docker-compose up`で作成されたすべてのリソース（コンテナ、ネットワーク、ボリューム）を停止および削除します。これにより、全てがクリーンな状態に戻ります。なお、`down`コマンドはデフォルトではイメージを削除しません。イメージも削除したい場合は、`--rmi all`オプションを使用します。

したがって、次回`docker-compose up`を実行する際に全てがクリーンな状態から開始したい場合、またはリソースを節約したい場合には`docker-compose down`を使うと良いでしょう。それ以外の場合、特に開発中やテスト中は`Ctrl+C`で十分なことが多いです。

ただし、`docker-compose down`を使うことにより、ボリュームが削除されるため、データが失われる可能性があります。そのため、データを保持したい場合には注意が必要です。この問題を回避するために、データを保持するためのボリュームを定義するか、`-v`オプションを使用しないでください。
