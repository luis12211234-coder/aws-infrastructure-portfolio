# AWS Infrastructure Portfolio

AWS上でのインフラ設計・構築と、障害時の挙動の検証に取り組む個人ポートフォリオです。

## 01. EC2上のWebサービスの可用性向上

単一EC2で稼働するWebサービスを、Application Load Balancerと2つのAZにまたがるEC2 Auto Scalingグループで再構成しました。EC2を1台停止した際、最初の失敗から60秒間の成功リクエストは単一EC2で0/29件、改善後は30/45件でした。Auto Scalingが代替EC2を起動し、正常なターゲットが2台に戻ることも確認しました。

**進捗**：構築・検証完了  
**ディレクトリ**：[01-ec2-high-availability/](./01-ec2-high-availability/)  
**検証結果**：[検証レポート](./01-ec2-high-availability/VERIFICATION.md)

## 02. 店舗別売上CSVの集計・再処理

S3にアップロードされた店舗別の売上CSVを、SQSを経由してLambdaで集計します。日付形式の違いによる処理エラーを再現し、失敗したメッセージがデッドレターキュー（DLQ）に移動することを確認します。日付の読み取り処理を修正した後、元のCSVを使って再処理し、集計結果を確認します。

**進捗**：計画中  
**ディレクトリ**：[02-sales-csv-reprocessing/](./02-sales-csv-reprocessing/)
