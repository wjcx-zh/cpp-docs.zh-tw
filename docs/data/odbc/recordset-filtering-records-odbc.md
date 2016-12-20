---
title: "資料錄集：篩選資料錄 (ODBC) | Microsoft Docs"
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
  - "資料 [MFC], 篩選"
  - "篩選資料錄集"
  - "篩選條件 [C++], recordset 物件"
  - "ODBC 資料錄集 [C++], 篩選資料錄"
  - "資料錄集 [C++], 篩選"
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：篩選資料錄 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 本主題說明如何篩選資料錄集，以便其僅選取可用資料錄的特定子集。  例如，您可能只想要選取一個諸如 MATH101 之特定課程的班級。  篩選條件是一個由 SQL **WHERE** 子句定義的搜尋條件。  當架構將它附加至資料錄集的 SQL 陳述式時，**WHERE** 子句便會限制選取。  
  
 您必須在建構資料錄集的物件後，於呼叫其 **Open** 成員函式前 \(對於先前已經呼叫 **Open** 成員函式之現有資料錄集物件，則是在呼叫 **Requery** 成員函式前\) 先建立資料錄集的篩選條件。  
  
#### 若要指定資料錄集物件的篩選條件  
  
1.  建構一個新的資料錄集物件 \(或準備對一個現有物件呼叫 **Requery**\)。  
  
2.  設定物件的 [m\_strFilter](../Topic/CRecordset::m_strFilter.md) 資料成員值。  
  
     篩選是 null 結尾字串，包含了 SQL **WHERE** 子具的內容，但不包含關鍵字 **WHERE**。  例如，使用：  
  
    ```  
    m_pSet->m_strFilter = "CourseID = 'MATH101'";  
    ```  
  
     not  
  
    ```  
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";  
    ```  
  
    > [!NOTE]
    >  上述所顯示的常值字串 "MATH101" 有單引號。  在 ODBC SQL 規格中，單引號是用來表示一個字元字串常值。  如需您的 DBMS 在此情形時的引號需求之詳細資訊，請參閱您的 ODBC 驅動程式文件。  這個主題的結尾附近也有進一步討論此語法。  
  
3.  設定任何您需要的其他選項，例如排序順序、鎖定模式或參數。  指定參數尤其有用。  如需參數化篩選的詳細資訊，請參閱[資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
4.  為新的物件呼叫 **Open** \(或為先前開啟過的物件呼叫 **Requery**\)。  
  
> [!TIP]
>  在您的篩選條件中使用參數，可能是最有效率的擷取資料錄方法。  
  
> [!TIP]
>  在[聯結](../../data/odbc/recordset-performing-a-join-odbc.md)資料表中，以及根據在執行階段時取得或計算來的資訊使用[參數](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)的情況下，資料錄集篩選條件是非常有用的。  
  
 資料錄集只會選取那些符合您指定之搜尋條件的資料錄。  例如，若要指定上述說明的課程篩選條件 \(假設已設定 `strCourseID` 變數為 "MATH101"\)，請執行下列步驟：  
  
```  
// Using the recordset pointed to by m_pSet  
  
// Set the filter  
m_pSet->m_strFilter = "CourseID = " + strCourseID;   
  
// Run the query with the filter in place  
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )  
  
// Use the recordset  
```  
  
 資料錄集包含所有 MATH101 之班級的資料錄。  
  
 請注意上述範例中已經使用字串變數設定了篩選字串。  這是一般的用法。  但假設您想要將課程 ID 指定為常值 100。  下面程式碼示範了使用一個常值來正確設定篩選字串的方式：  
  
```  
m_strFilter = "StudentID = '100'";   // correct  
```  
  
 請記得使用單引號字元；若您直接設定篩選字串，篩選字串便**不**會是您預期的結果：  
  
```  
m_strFilter = "StudentID = 100";   // incorrect for some drivers  
```  
  
 上述的引號是遵循 ODBC 規格，但某些 DBMS 可能需要其他的引號字元。  如需詳細資訊，請參閱 [SQL：自訂資料錄集的 SQL 陳述式 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。  
  
> [!NOTE]
>  如果您選擇藉由傳遞自己的 SQL 字串給 **Open** 來覆寫資料錄集的預設 SQL 字串，且您自訂的字串中有 **WHERE** 子句時，便不應該設定篩選條件。  如需覆寫預設 SQL 的詳細資訊，請參閱 [SQL：自訂資料錄集的 SQL 陳述式 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：排序資料錄 \(ODBC\)](../../data/odbc/recordset-sorting-records-odbc.md)   
 [資料錄集：資料錄集選取資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [資料錄集：資料錄集更新資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [資料錄集：鎖定資料錄 \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)