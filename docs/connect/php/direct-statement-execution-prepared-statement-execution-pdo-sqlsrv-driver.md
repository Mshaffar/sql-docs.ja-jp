---
title: 直接ステートメント - 準備されたステートメントの実行 PDO_SQLSRV ドライバー | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1ca9ab0e2846ddff98b6a0d7b626ae6757517a2d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928006"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdo_sqlsrv-driver"></a>Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver (PDO_SQLSRV ドライバーでの直接ステートメント実行と準備されたステートメントの実行)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、PDO::SQLSRV_ATTR_DIRECT_QUERY 属性を使用して、準備されたステートメントの実行である既定ではなく、直接のステートメントの実行を指定する方法について説明します。 パラメーターのバインドを使用してステートメントが複数回実行される場合、準備されたステートメントを使用すると、パフォーマンスが向上する可能性があります。  
  
## <a name="remarks"></a>解説  
ドライバーによるステートメントの準備を行わずに [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントをサーバーに直接送信する場合は、PDO::SQLSRV_ATTR_DIRECT_QUERY 属性を [PDO::setAttribute](../../connect/php/pdo-setattribute.md) を使って (または [PDO::__construct](../../connect/php/pdo-construct.md) に渡されるドライバー オプションとして)、または [PDO::prepare](../../connect/php/pdo-prepare.md) を呼び出すときに設定できます。 既定では、PDO::SQLSRV_ATTR_DIRECT_QUERY の値は False です (準備されたステートメントの実行を使用します)。  
  
[PDO::query](../../connect/php/pdo-query.md) を使用する場合は、直接実行が必要になることがあります。 [PDO::query](../../connect/php/pdo-query.md) を呼び出す前に、[PDO::setAttribute](../../connect/php/pdo-setattribute.md) を呼び出し、PDO::SQLSRV_ATTR_DIRECT_QUERY を True に設定します。  [PDO::query](../../connect/php/pdo-query.md) への各呼び出しは、PDO::SQLSRV_ATTR_DIRECT_QUERY の異なる設定で実行できます。  
  
[PDO::prepare](../../connect/php/pdo-prepare.md) と [PDOStatement::execute](../../connect/php/pdostatement-execute.md) を使用し、バインドされたパラメーターを使用してクエリを複数回実行すると、準備されたステートメントの実行によって、繰り返しクエリの実行が最適化されます。  この場合は、ドライバー オプション配列パラメーターで PDO::SQLSRV_ATTR_DIRECT_QUERY を False に設定して [PDO::p repare](../../connect/php/pdo-prepare.md) を呼び出します。 必要に応じて、PDO::SQLSRV_ATTR_DIRECT_QUERY を False に設定して準備されたステートメントを実行できます。  
  
[PDO::p repare](../../connect/php/pdo-prepare.md) を呼び出した後、準備されたクエリの実行時に PDO::SQLSRV_ATTR_DIRECT_QUERY の値を変更することはできません。  
  
あるクエリに、前のクエリで設定されたコンテキストが必要な場合は、PDO::SQLSRV_ATTR_DIRECT_QUERY を True に設定してクエリを実行します。 たとえば、クエリで一時テーブルを使用する場合、PDO::SQLSRV_ATTR_DIRECT_QUERY を True に設定する必要があります。  
  
前のステートメントのコンテキストが必要な場合、PDO::SQLSRV_ATTR_DIRECT_QUERY を True に設定する必要があることを示す例を次に示します。 このサンプルは、クエリが直接実行されたときに、プログラム内の後続のステートメントでのみ使用できる一時テーブルを使用します。  
  
> [!NOTE]
> ストアド プロシージャを呼び出すためのクエリであり、このストアド プロシージャで一時テーブルが使用される場合は、代わりに [PDO::exec](../../connect/php/pdo-exec.md) を使用します。

```  
<?php  
   $conn = new PDO('sqlsrv:Server=(local)', '', '');  
   $conn->setAttribute(constant('PDO::SQLSRV_ATTR_DIRECT_QUERY'), true);  
  
   $stmt1 = $conn->query("DROP TABLE #php_test_table");  
  
   $stmt2 = $conn->query("CREATE TABLE #php_test_table ([c1_int] int, [c2_int] int)");  
  
   $v1 = 1;  
   $v2 = 2;  
  
   $stmt3 = $conn->prepare("INSERT INTO #php_test_table (c1_int, c2_int) VALUES (:var1, :var2)");  
  
   if ($stmt3) {  
      $stmt3->bindValue(1, $v1);  
      $stmt3->bindValue(2, $v2);  
  
      if ($stmt3->execute())  
         echo "Execution succeeded\n";       
      else  
         echo "Execution failed\n";  
   }  
   else  
      var_dump($conn->errorInfo());  
  
   $stmt4 = $conn->query("DROP TABLE #php_test_table");  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQL Server 用 Microsoft Drivers for PHP のためのプログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
  
