# Vantiq 1-day Workshop 概要説明

この Workshop では、複数のポンプのリアルタイムデータを取得し、ポンプの異常を検知するシステムを構築します。  

## Workshop を行うにあたり注意する点

- Workshop を行うにあたり、講師がいる場合と講師がいない場合で、内容の一部が異なります。  
- 内容が異なる部分の説明は、それぞれ折りたたまれています。  
  クリックすると表示されます。  
- 講師の方は事前に **Data Generator** と **MQTTブローカー** を用意しておいてください。（[データジェネレータの準備](0-03_DataGenerator.md)）  

## ポンプ故障検知システム

下記の要件を満たす **ポンプ故障検知システム** の実装を通じてVantiqの基本機能を学んでいきます。  

* __前提__
  * ポンプが５台あり、それぞれに __温度センサー__ と  __回転数センサー__ が付いている
* __実装する機能__
  * 温度が __200__  __度以上__ 、かつ回転数が __4000__  __回以上__ の状態が __20__  __秒間続いた__ 際に「故障」として検出する

## ポンプ故障検知システムの処理の流れ

5台のポンプは **温度データ** や **回転数データ** などを **MQTT Broker Server** へ **Publish（送信）** します。  
VANTIQ は 各ポンプのデータを取得するために **MQTT Broker Server** へ **Subscribe（受信）** しにいきます。  
**MQTT Broker Server** は各ポンプのデータの受け渡しを中継する役割を担います。  

![ポンプ故障検知システムの処理の流れ](../../imgs/readme/slide3.png)   
&nbsp;&nbsp;&nbsp; **＊ Pump Failure Detection System: ポンプの故障を検知**

## Vantiq 1-day Workshop での処理の流れ
このWorkshopにおいては、実際のセンサー/デバイスの代わりに、Dummyデータを MQTT Broker Server へ Publish します。  
Dummyデータの Publish は手作業でも行えますが、このWorkshopにおいてはポンプのDummyデータを自動的に Publish してくれる **Data Generator** を使用します。  
**Data Generator** は **５台分のポンプ** の **温度** と **回転数** のデータを **ランダムに Publish** します。

![Vantiq 1-day Workshop での処理の流れ](../../imgs/readme/slide4.png)  
&nbsp;&nbsp;&nbsp; **＊ Pump Failure Detection System: ポンプの故障を検知**

## Workshopで使用するマテリアル

<details>
<summary>講師がいる場合</summary>

* Labs：Vantiq 1-day Workshop の手順書
  * 01~06
  * 追加課題: 混雑検出アプリ開発課題
* Lectures:　説明資料
* Materials：手順書で使用する[素材ファイル](../../conf)
  * Pumps\.json
</details>

<details>
<summary>講師がいない場合</summary>

* Labs：Vantiq 1-day Workshop の手順書
  * 01~06
  * 追加課題: 混雑検出アプリ開発課題
* Lectures:　説明資料
* Materials：手順書で使用する[素材ファイル](../../conf)
  * TraingDataGen\.zip
  * Pumps\.json
</details>


## Workshopで準備が必要なもの

<details>
<summary>講師がいない場合</summary>

- MQTT Broker（※Internetからアクセスできるもの）
  - MQTT Broker の一例
    - Amazon MQ
    - Mosquitto
    - [HIVEMQ Public MQTT Broker](https://www.hivemq.com/public-mqtt-broker/)  

  参考: [【速報】新サービスAmazon MQを早速使ってみた！](https://dev.classmethod.jp/articles/re-invent-2017-amazon-mq-first-impression/)
</details>


## Vantiq 1-day Workshop の内容

* 以下の内容を通してポンプの故障検知システムを作成します。
  * __Lab01__  __準備__
    * ネームスペースやデータジェネレータの準備
  * __Lab02 Types__  __（タイプ）__
    * データベースのテーブルのような機能
  * __Lab03 Sources__  __（ソース）__
    * データの送受信で使う機能
  * __Lab04 App Builder__  __（アプリケーションビルダー）__
    * 受信したイベントの処理ロジックの作成
* 以下の内容を通してVantiqと外部システム連携を行います。
  * __Lab05 REST API__
    * 外部システムからVantiqリソースを操作します。
  * __Lab06 REMOTE Source__
    * Vantiqから外部システムのAPIを呼び出します。


## Course Agenda

| Session # | Session                                 |  Type   | Contents Description                               | Duration (m) | Material                                                                                                                    |
|:---------:| --------------------------------------- |:-------:| -------------------------------------------------- |:------------:| --------------------------------------------------------------------------------------------------------------------------- |
|     1     | VANTIQ で開発する上での基本事項         | Lecture |                                                    |      10      | [01_Basics](1-01_Basics.md)                                                                                                 |
|     2     | 準備         |   Lab   | Namespace やデータジェネレータの準備                           |      5 ～ 15      | [Lab01_Preparation](2-Lab01_Preparation.md)                                                                                 |
|     3     | Vantiq の基本リソース                   | Lecture | Vantiqアプリケーションを構成する最も基本なリソース |      15      | [00_BasicResources](0-10_BasicResources.md)                                                                                 |
|     4     | Types (タイプ)                          |   Lab   | データベースのテーブルのような機能                 |      20      | [Lab02_Types](3-Lab02_Types.md)                                                                                             |
|     5     | Source (ソース)                         |   Lab   | データの送受信で使う機能                           |      20      | [Lab03_Sources](4-Lab03_Sources.md)                                                                                         |
|     6     | App Builder の紹介                      | Lecture |                                                    |      15      | [02_AppBuilder](5-02_AppBuilder.md)                                                                                         |
|     7     | App Builder (アプリケーション ビルダー) |   Lab   | 受信したイベントの処理ロジックの作成               |      45      | [Lab04_AppBuilder](6-Lab04_AppBuilder.md)                                                                                   |
|     8     | Lab 04 までの復習                       | Lecture |                                                    |      15      | [03_Review](7-03_Review.md)                                                                                                 |
|     9     | Q&A                                     |         | 質疑応答                                           |      15      |                                                                                                                             |
|    10     | VANTIQ REST API                         |   Lab   | Vantiq 1-day Workshop の次のステップ               |              | [Lab05_VANTIQ_REST_API](a08-Lab05_VANTIQ_REST_API.md)                                                                       |
|    11     | 他サービスとの連携                      |   Lab   | Vantiq 1-day Workshop の次のステップ               |              | [Lab06_Integrate_other_services](a09-Lab06_Integrate_other_services.md)                                                     |
|    12     | Vantiqのリソース全般の紹介              |         | Reference                                          |              | [実例を通して Vantiq のリソースを理解する](../../../vantiq-resources-introduction/docs/jp/Vantiq_resources_introduction.md) |
|    13     | 混雑検出アプリ開発課題                  |   Lab   | Vantiq 1-day Workshop の次のステップ               |              | [混雑検出課題アプリ](a10-dev01_detect_congestion_app.md)                                                                    |


＊上記のセッションを修了後、開発者の方はより深く理解をするため、[Vantiq アプリケーション開発者コース＆レベル1認定試験](https://community.vantiq.com/courses/%e3%82%a2%e3%83%97%e3%83%aa%e3%82%b1%e3%83%bc%e3%82%b7%e3%83%a7%e3%83%b3%e9%96%8b%e7%99%ba%e8%80%85-level-1-%e3%82%b3%e3%83%bc%e3%82%b9-%e6%97%a5%e6%9c%ac%e8%aa%9e/)（要ログイン）の受講をお勧めします。

## 参考情報
[トラブルシューティング](./troubleshootings.md)
