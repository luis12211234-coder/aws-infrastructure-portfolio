# AWS Infrastructure Portfolio

AWS上でのインフラ設計・構築と、障害時の挙動の検証に取り組む個人ポートフォリオです。

## 01. EC2上のWebサービスの可用性向上

単一EC2で稼働するWebサービスを、Application Load Balancerと2つのAZにまたがるEC2 Auto Scalingグループで再構成しました。EC2を1台停止した際、最初の失敗から60秒間の成功リクエストは単一EC2で0/29件、改善後は30/45件でした。Auto Scalingが代替EC2を起動し、正常なターゲットが2台に戻ることも確認しました。

**進捗**：構築・検証完了  
**ディレクトリ**：[01-ec2-high-availability/](./01-ec2-high-availability/)  
**検証結果**：[検証レポート](./01-ec2-high-availability/VERIFICATION.md)

## 02. 店舗別売上CSVの集計・再処理

S3にアップロードされた売上CSVをSQSとLambdaで集計しました。日付形式の違いで処理に失敗したB店のメッセージをDLQで確認し、Lambdaの修正後に元のキューへ戻しました。CSVを再アップロードせず、650円の集計結果を出力用S3に保存できることを確認しました。

**進捗**：構築・検証完了  
**ディレクトリ**：[02-sales-csv-reprocessing/](./02-sales-csv-reprocessing/)  
**検証結果**：[検証レポート](./02-sales-csv-reprocessing/VERIFICATION.md)
