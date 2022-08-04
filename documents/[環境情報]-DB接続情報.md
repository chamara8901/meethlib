---
title: DB接続情報
categories:
  - MEETH
---
# [環境情報]-DB接続情報

- DEV、STG、PRODの踏み台サーバからそれぞれ、RDSのDEV、STG、PRODへ接続
- DBはRDS、接続は踏み台サーバ経由、事務所↔踏み台サーバは鍵認証

## DEV環境
- 踏み台サーバ
  - host : 3.112.42.81
  - user : ec2-user
- DB
  - endpoint : meeth-rds-dev.czteios10ewk.ap-northeast-1.rds.amazonaws.com
  - user : admin
  - pass : vaf3cYlM9LdcomH92z6sr2^,kM=AM8

## STG環境
- 踏み台サーバ
  - host : 54.95.250.171
  - user : ec2-user
- DB
  - endpoint : meeth-rds-stg.czteios10ewk.ap-northeast-1.rds.amazonaws.com
  - user : admin
  - pass : NOazdijLF2DfF_=dqO,M0=2c0fSAfJ

## PROD環境
- 踏み台サーバ
  - host : 52.199.71.78
  - user : ec2-user
- DB
  - endpoint : meeth-rds-prod2-recover.czteios10ewk.ap-northeast-1.rds.amazonaws.com
  - user : admin
  - pass : mxMj8k9PZ4e3vWhk_6.ame895j1k3U
  
