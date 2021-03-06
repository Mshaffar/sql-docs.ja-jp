---
title: sp_server_info (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_server_info
- sp_server_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_server_info
ms.assetid: 2dc2c262-3cfa-4a84-8127-3632ba583543
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a83d216b0830b035da72ad579a2448a12f41adba
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82810472"
---
# <a name="sp_server_info-transact-sql"></a>sp_server_info (Transact-sql)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データベースゲートウェイ、または基になるデータソースの属性名と一致する値の一覧を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_server_info [[@attribute_id = ] 'attribute_id']  
```  
  
## <a name="arguments"></a>引数  
`[ @attribute_id = ] 'attribute_id'`属性の整数 ID を示します。 *attribute_id*は**int**,、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 None  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**ATTRIBUTE_ID**|**int**|属性の ID 番号。|  
|**ATTRIBUTE_NAME**|**varchar (** 60 **)**|属性名です。|  
|**ATTRIBUTE_VALUE**|**varchar (** 255 **)**|属性の現在の設定です。|  
  
 次の表に、属性の一覧を示します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)]ODBC クライアントライブラリでは、接続時に属性**1**、 **2**、 **18**、 **22**、および**500**が現在使用されています。  
  
|ATTRIBUTE_ID|ATTRIBUTE_NAME の説明|ATTRIBUTE_VALUE|  
|-------------------|---------------------------------|----------------------|  
|**1**|DBMS_NAME|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**2**|DBMS_VER|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] - *x.y*|  
|"**10**"|OWNER_TERM|owner|  
|**11**|TABLE_TERM|table|  
|**12**|MAX_OWNER_NAME_LENGTH|128|  
|**13**|TABLE_LENGTH<br /><br /> テーブル名の最大文字数です。|128|  
|**14**|MAX_QUAL_LENGTH<br /><br /> テーブル修飾子の名前 (3 つの要素から成る名前の最初の部分) の最大の長さです。|128|  
|**15**|COLUMN_LENGTH<br /><br /> 列名の最大文字数です。|128|  
|**まで**|IDENTIFIER_CASE<br /><br /> データベース内のユーザー定義の名前 (テーブル名、列名、ストアド プロシージャ名) です。大文字か小文字かは、システム カタログ内でオブジェクトの名前に従います。|SENSITIVE|  
|**a3**|TX_ISOLATION<br /><br /> SQL-92 で定義されている分離レベルに対応する、サーバーが想定する初期トランザクション分離レベルを指定します。|2|  
|**18**|COLLATION_SEQ<br /><br /> このサーバーの文字セットの順序です。|charset=iso_1 sort_order=dictionary_iso charset_num=1 sort_order_num=51|  
|**21**|SAVEPOINT_SUPPORT<br /><br /> 基になる DBMS が、名前付きセーブポイントをサポートするかどうかを示します。|○|  
|**20@@**|MULTI_RESULT_SETS<br /><br /> 基になるデータベースまたはゲートウェイ自体が複数の結果セットをサポートするかどうかを指定します (複数のステートメントをゲートウェイを介して送信し、複数の結果セットをクライアントに返すことができます)。|○|  
|**22**|ACCESSIBLE_TABLES<br /><br /> **Sp_tables**であるかどうかを指定します。ゲートウェイは、現在のユーザー (つまり、少なくともテーブルに対する SELECT 権限を持つユーザー) がアクセスできるテーブル、ビューなどを返します。|○|  
|**100**|USERID_LENGTH<br /><br /> ユーザー名の最大文字数を示します。|128|  
|**101**|QUALIFIER_TERM<br /><br /> DBMS ベンダーの用語で、テーブル修飾子 (3 つの要素から成る名前の最初の部分) を示します。|database|  
|**102**|NAMED_TRANSACTIONS<br /><br /> 基になる DBMS が名前付きトランザクションをサポートするかどうかを指定します。|○|  
|**103**|SPROC_AS_LANGUAGE<br /><br /> ストアド プロシージャを言語イベントとして実行できるかどうかを示します。|○|  
|**104**|ACCESSIBLE_SPROC<br /><br /> **Sp_stored_procedures**であるかどうかを指定します。ゲートウェイは、現在のユーザーが実行可能なストアドプロシージャだけを返します。|○|  
|**105**|MAX_INDEX_COLS<br /><br /> DBMS のインデックスに含まれる列の最大数を指定します。|16|  
|**106**|RENAME_TABLE<br /><br /> テーブルの名前を変更できるかどうかを指定します。|○|  
|**107**|RENAME_COLUMN<br /><br /> 列の名前を変更できるかどうかを指定します。|○|  
|**108**|DROP_COLUMN<br /><br /> 列を削除できるかどうかを示します。|○|  
|**109**|INCREASE_COLUMN_LENGTH<br /><br /> 列のサイズを大きくできるかどうかを示します。|○|  
|**110**|DDL_IN_TRANSACTION<br /><br /> DDL ステートメントをトランザクションで使用できるかどうかを示します。|○|  
|**111**|DESCENDING_INDEXES<br /><br /> 降順のインデックスがサポートされるかどうかを示します。|○|  
|**112**|SP_RENAME<br /><br /> ストアドプロシージャの名前を変更できるかどうかを指定します。|○|  
|**113**|REMOTE_SPROC<br /><br /> ストアド プロシージャを DB-Library のリモート ストアド プロシージャ関数を使用して実行できるかどうかを示します。|○|  
|**500**|SYS_SPROC_VERSION<br /><br /> 現在実装されているストアド プロシージャ カタログのバージョンを示します。|現在のバージョン番号|  
  
## <a name="remarks"></a>Remarks  
 **sp_server_info**は、ODBC で**SQLGetInfo**によって提供される情報のサブセットを返します。  
  
## <a name="permissions"></a>アクセス許可  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のカタログストアドプロシージャ](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
