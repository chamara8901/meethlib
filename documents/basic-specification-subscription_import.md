---
title: basic-specification-order_import
categories:
  - MEETH
---
```
・CSV1行ずつ処理
　・shopifyのsubscription_idが既に登録されているかチェック (ある場合、skip)
　・メールアドレスの存在チェック (ない場合、skip)
　・Subscriptionテーブル新規登録
　・SubscriptionDetailsテーブル新規登録
```