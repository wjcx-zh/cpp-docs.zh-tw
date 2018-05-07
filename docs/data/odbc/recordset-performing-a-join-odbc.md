---
title: 資料錄集： 執行聯結 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0be740a57f5c455b971dd23575401c666bf0723c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-performing-a-join-odbc"></a>資料錄集：執行聯結 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
## <a name="what-a-join-is"></a>什麼是聯結  
 聯結作業，常見的資料存取工作，可讓您使用多個使用單一資料錄集物件的資料表中的資料。 聯結兩個或多個資料表會產生可以包含的每個資料表，資料行，但會顯示為您的應用程式的單一資料表的資料錄集。 有時聯結會使用所有的資料行中所有資料表，但有時候 SQL**選取**子句聯結中的只使用某些的每個資料表中的資料行。 資料庫類別支援唯讀的聯結，但不是能更新聯結。  
  
 若要選取包含聯結的資料表中的資料行的記錄，您需要下列項目：  
  
-   資料表清單，其中包含所要加入的所有資料表的名稱。  
  
-   資料行清單，其中包含所有參與的資料行的名稱。 具有相同名稱但不同資料表中的資料行被限定資料表名稱。  
  
-   篩選 (SQL**其中**子句) 指定的資料表會聯結的資料行。 此篩選條件會採用"Table1.KeyCol = Table2.KeyCol 」 並實際完成聯結。  
  
 您也可以納入方程式多對資料行，每個配對會以 SQL 關鍵字相同的方式加入兩個以上資料表**AND**。  
  
## <a name="see-also"></a>另請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 宣告預先定義的查詢 (ODBC) 的類別](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)   
 [資料錄集： 宣告資料表 (ODBC) 的類別](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [資料錄集：重新查詢資料錄集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)