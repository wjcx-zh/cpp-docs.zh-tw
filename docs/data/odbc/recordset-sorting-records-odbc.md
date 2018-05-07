---
title: 資料錄集： 排序資料錄 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ddb92016b7b911fc86f2feab27a698ce7fa55c45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-sorting-records-odbc"></a>資料錄集：排序資料錄 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 本主題說明如何排序資料錄集。 您可以指定將依據排序的一或多個資料行，而且您可以指定遞增或遞減順序 (`ASC`或**DESC**;`ASC`是預設值) 每個指定資料行。 例如，如果您指定兩個資料行時，記錄來排序第一次命名的第一個資料行，然後在名為第二個資料行上。 SQL **ORDER BY**子句會定義排序。 架構會將附加**ORDER BY**子句資料錄集的 SQL 查詢，請選取範圍的排序子句控制項。  
  
 建構物件之後但在您呼叫之前，您必須建立資料錄集的排序次序其**開啟**成員函式 (或在呼叫之前**Requery**現有的資料錄集物件的成員函式其**開啟**先前呼叫成員函式)。  
  
#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>若要指定排序次序的資料錄集物件  
  
1.  建構一個新的資料錄集物件 (或準備呼叫**Requery**現有)。  
  
2.  設定物件的值[m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)資料成員。  
  
     排序是以 null 結束的字串。 它包含的內容**ORDER BY**子句，但不是關鍵字**ORDER BY**。 例如，使用：  
  
    ```  
    recordset.m_strSort = "LastName DESC, FirstName DESC";  
    ```  
  
     not  
  
    ```  
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";  
    ```  
  
3.  設定需要例如篩選、 鎖定模式或參數的其他選項。  
  
4.  呼叫**開啟**新物件 (或**Requery**現有的物件)。  
  
 選取的記錄會排序所指定。 例如，若要排序的一組以遞減順序姓氏，然後再按照名字的學生記錄，執行下列作業：  
  
```  
// Construct the recordset  
CStudentSet rsStudent( NULL );  
// Set the sort  
rsStudent.m_strSort = "LastName DESC, FirstName DESC";  
// Run the query with the sort in place  
rsStudent.Open( );  
```  
  
 資料錄集包含所有的學生記錄，以遞減順序 (從 Z 到 A)，依排序姓氏，然後第一個名稱。  
  
> [!NOTE]
>  如果您選擇覆寫資料錄集的預設 SQL 字串傳遞您自己的 SQL 字串**開啟**，請勿設定排序，如果您的自訂字串具有**ORDER BY**子句。  
  
## <a name="see-also"></a>另請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)