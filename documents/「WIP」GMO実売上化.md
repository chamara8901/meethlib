---
title: 「WIP」GMO実売上化
categories:
  - MEETH
---
## 目的
新Meethにおいて、クレジット決済が仮売上までしか処理されない。  
実売上を実施しないと、入金されないため必須の作業。  
期限は仮売上から60日。  
[参考リンク（GMO）](https://faq.gmo-pg.com/service/Detail.aspx?id=2146)

## 作業概要
作業方法は３種類ある。
1. 一件ずつ処理する。  
　個別対応の場合に実施。
2. 一括処理（画面）  
　500件ずつ処理できる。CSV等のミスを考えると当面この処理で良さそう。
3. 一括処理（CSV）  
　CSVで一括処理を行う。注文数が5,000件を超える、もしくは事前の突合チェックで簡易生成できるなら良さそう。  
[参考リンク（GMO）](https://faq.gmo-pg.com/service/Detail.aspx?id=950)

## 作業詳細
1. 出荷データの統合
* 対象期間の出荷データをGoogle Driveから取得
 https://drive.google.com/drive/folders/1lsueSftemzHsm5HINNd2cOYHGlHCW-8s
* 出荷データファイルを統合
* エクセルに読み込む
* 決済方法=credit_card以外を削除
* 表示受注番号で一意にする
2. GMO仮売上データの取得
* GMO管理画面にログイン
* ヘッダーの選択でSHOPを選択
* レフトナビの都度決済>クレジットカードを選択
* 状態=仮売上、処理日時=出荷データの注文期間を広めに指定し検索
* CSVダウンロードから会員IDでCSVダウンロード
* エクセルに読みこむ
3. 注文IDとオーダーIDのマッピングデータ取得
* VPN接続
* DBに接続し下記のクエリを実行し、マッピングデータを取得  
　`select id, customer_id, shopify_order_id, gmo_order_id, created_at from meeth.orders o where id > 1000000`  
* 
4. 出荷データ（注文ID）- マッピングデータ - GMO仮売上データの紐づけ
5. 出荷データ（注文ID）- GMO仮売上データが紐づいたものを実売上化 -- (1)
6. エラーケースの対処1:マッピングデータにGMOオーダーIDがない→ShopifyオーダーIDが存在すればBOLD側で決済済みのため対象外とする。
7. エラーケースの対処2:マッピングデータにGMOオーダーIDがない→顧客IDがある場合は顧客ID
8. エラーケースの対処3:マッピングデータにGMOオーダーIDがあるがGMOにオーダーIDが存在しない

