---
title: azdata bdc status リファレンス
titleSuffix: SQL Server big data clusters
description: azdata bdc status コマンドに関するリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 01518e62d67c27a72bf1e0d78d249b1a64276883
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "74821005"
---
# <a name="azdata-bdc-status"></a>azdata bdc status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

以下の記事では、`azdata` ツールの `bdc status` コマンドに関するリファレンスを提供します。 `azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc status show](#azdata-bdc-status-show) | BDC の状態を表示します。
## <a name="azdata-bdc-status-show"></a>azdata bdc status show
BDC の状態を表示します。
```bash
azdata bdc status show [--resource -r] 
                       [--all -a]
```
### <a name="examples"></a>例
ユーザーがログインしている BDC の状態。
```bash
azdata bdc status show
```
リソースのすべてのインスタンスを含む BDC の状態。
```bash
azdata bdc status show --all
```
制御リソースが含まれるサービスの BDC の状態。
```bash
azdata bdc status show --resource control
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--resource -r`
このリソースに関連付けられているサービスを取得します。
#### `--all -a`
サービス内の各リソースのすべてのインスタンスを表示します。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org/) を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。

## <a name="next-steps"></a>次のステップ

`azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください。 `azdata` ツールのインストール方法の詳細については、[SQL Server 2019 ビッグ データ クラスターを管理する azdata のインストール](deploy-install-azdata.md)に関するページを参照してください。
