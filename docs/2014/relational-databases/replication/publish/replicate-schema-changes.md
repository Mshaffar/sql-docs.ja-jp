---
title: スキーマ変更のレプリケート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: c09007f0-9374-4f60-956b-8a87670cd043
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 84918dd3f50d129485911fc880e67c0152fa905c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "73882244"
---
# <a name="replicate-schema-changes"></a>スキーマ変更のレプリケート
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、スキーマの変更をレプリケートする方法について説明します。  
  
 パブリッシュされたアーティクルに対し、次のようなスキーマ変更を行った場合、変更内容が既定で [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバーに反映されます。  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **スキーマの変更をレプリケートするために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   ALTER TABLE ...DROP COLUMN ステートメントは、スキーマ変更のレプリケーションを無効にした場合でも、サブスクリプションに削除対象の列が含まれているすべてのサブスクライバーに必ずレプリケートされます。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションに対するスキーマ変更をレプリケートしない場合は、 **[パブリケーションのプロパティ - \<パブリケーション>]** ダイアログ ボックスでスキーマ変更のレプリケーションを無効にします。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。  
  
#### <a name="to-disable-replication-of-schema-changes"></a>スキーマ変更のレプリケーションを無効にするには  
  
1.  **[パブリケーションのプロパティ - \<パブリケーション>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、 **[スキーマ変更のレプリケート]** プロパティの値を **[False]** に設定します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     特定のスキーマ変更だけを反映させるには、スキーマを変更する前にプロパティを **[True]** に設定し、変更後に **[False]** に設定します。 逆に、ほとんどのスキーマ変更を反映するには、スキーマ変更前にプロパティを **[False]** に設定し、変更後に **[True]** に設定します。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーションのストアド プロシージャを使用すると、これらのスキーマ変更をレプリケートするかどうかを指定できます。 どのストアド プロシージャを使用するかは、パブリケーションの種類によって異なります。  
  
#### <a name="to-create-a-snapshot-or-transactional-publication-that-does-not-replicate-schema-changes"></a>スキーマ変更をレプリケートしないスナップショット パブリケーションまたはトランザクション パブリケーションを作成するには  
  
1.  パブリッシャー側のパブリケーションデータベースに対して[sp_addpublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)を実行します。このとき、 ** \@replicate_ddl**には**0**の値を指定します。 詳しくは、「 [パブリケーションを作成](create-a-publication.md)」をご覧ください。  
  
#### <a name="to-create-a-merge-publication-that-does-not-replicate-schema-changes"></a>スキーマ変更をレプリケートしないマージ パブリケーションを作成するには  
  
1.  パブリッシャー側のパブリケーションデータベースに対して[sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行します。このとき、 ** \@replicate_ddl**には**0**の値を指定します。 詳しくは、「 [パブリケーションを作成](create-a-publication.md)」をご覧ください。  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションでスキーマ変更のレプリケートを一時的に無効化するには  
  
1.  スキーマ変更のレプリケーションを含むパブリケーションの場合は、 [sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)を実行します。このとき、 ** \@プロパティ**には**replicate_ddl**を** \@、値に**は**0**を指定します。  
  
2.  パブリッシュされたオブジェクトに対し、DDL コマンドを実行します。  
  
3.  Optional[Sp_changepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)を実行して、スキーマ変更のレプリケートを再度有効にします。 ** \@プロパティ**には**replicate_ddl**を** \@、値に**は**1**を指定します。  
  
#### <a name="to-temporarily-disable-replicating-schema-changes-for-a-merge-publication"></a>マージ パブリケーションでスキーマ変更のレプリケートを一時的に無効化するには  
  
1.  スキーマ変更のレプリケーションを含むパブリケーションの場合は、 [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。このとき、 ** \@プロパティ**には**replicate_ddl**を** \@、値に**は**0**を指定します。  
  
2.  パブリッシュされたオブジェクトに対し、DDL コマンドを実行します。  
  
3.  Optional[Sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行して、スキーマ変更のレプリケートを再度有効にします。 ** \@プロパティ**には**replicate_ddl**を** \@、値に**は**1**を指定します。  
  
## <a name="see-also"></a>参照  
 [パブリケーション データベースでのスキーマの変更](make-schema-changes-on-publication-databases.md)   
 [パブリケーション データベースでのスキーマの変更](make-schema-changes-on-publication-databases.md)  
  
  
