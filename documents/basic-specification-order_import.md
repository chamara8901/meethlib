---
title: basic-specification-order_import
categories:
  - MEETH
---
```
・CSV全読みして、{shopify_display_id => shopify_order_id } のハッシュ作成
・CSV1行ずつ処理
　・メールアドレスの存在チェック
　・注文のトータル金額がCSVに存在するか
　　・ある場合
　　　・注文データ新規作成
　　　・定期購入の注文かどうか
　　　　・定期購入IDと注文データ紐付け
　　　　・定期購入テーブルのprocessing_statusを更新 ※ 配送完了の場合
　　　・注文住所、配送先住所、注文詳細、Paymentテーブルにレコード新規作成
　　・ない場合
　　　既に登録されているshopify_order_idに紐づく注文データの注文詳細データを追加
```

