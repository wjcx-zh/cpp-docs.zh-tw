---
title: "資料錄集：排序資料錄 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ODBC 資料錄集, 排序"
  - "資料錄集, 排序"
  - "排序資料, 資料錄集資料"
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：排序資料錄 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 這個主題說明如何排序資料錄集。  您可指定一個或多個用來做為排序依據的資料行，也可以指定的每個指定資料行為遞增或遞減順序 \(`ASC` 或 **DESC**；預設設定是 `ASC`\)。  例如，如果指定兩個資料行，第一個命名的資料行上的資料錄會先進行排序，然後再排序第二個命名的資料行。  一個 SQL **ORDER BY** 子句將定義一個排序。  當架構將 **ORDER BY** 子句附加至資料錄集的 SQL 查詢時，該子句會控制選取的順序。  
  
 您必須在建構資料錄集物件之後，及呼叫其 **Open** 成員函式之前 \(對於先前已經呼叫 **Open** 成員函式之現有資料錄集物件，則是在呼叫 **Requery** 成員函式前\)，建立資料錄集的排序順序。  
  
#### 若要指定資料錄集物件的排序順序  
  
1.  建構一個新的資料錄集物件 \(或準備對一個現有物件呼叫 **Requery**\)。  
  
2.  設定物件的 [m\_strSort](../Topic/CRecordset::m_strSort.md) 資料成員值。  
  
     排序是一個以 Null 值結束的字串。  其包含了 **ORDER BY** 子句的內容，但不包括 **ORDER BY** 關鍵字。  例如，使用：  
  
    ```  
    recordset.m_strSort = "LastName DESC, FirstName DESC";  
    ```  
  
     not  
  
    ```  
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";  
    ```  
  
3.  設定任何您需要的其他選項，例如篩選條件、鎖定模式或參數。  
  
4.  為新物件呼叫 **Open** \(或為現有的物件呼叫 **Requery**\)。  
  
 選取資料錄會依指定排序。  例如，若要以遞減順序地依照姓氏，接著是名字的次序來排序一組學生資料錄，請執行下列步驟：  
  
```  
// Construct the recordset  
CStudentSet rsStudent( NULL );  
// Set the sort  
rsStudent.m_strSort = "LastName DESC, FirstName DESC";  
// Run the query with the sort in place  
rsStudent.Open( );  
```  
  
 資料錄集包含所有先以姓氏的遞減順序 \(Z 至 A\) 排序，再以名字的遞減順序排序的學生資料錄。  
  
> [!NOTE]
>  如果選擇藉由傳遞擁有的 SQL 字串給 **Open** 來覆寫資料錄集的預設 SQL 字串，而且自訂字串中有 **ORDER BY** 子句，則請不要設定排序。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [資料錄集：篩選資料錄 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)