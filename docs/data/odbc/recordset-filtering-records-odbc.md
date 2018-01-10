---
title: "資料錄集： 篩選資料錄 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b6d6e8b41e67c9f33d643a2f64c7bdf2d2251eff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-filtering-records-odbc"></a>資料錄集：篩選資料錄 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 本主題說明如何篩選資料錄集，使它會選取可用的資料錄對特定子集。 例如，您可以選取只為特定的課程中，例如 MATH101 類別區段。 篩選是由 SQL 的內容定義的搜尋條件**其中**子句。 當架構將它附加至資料錄集的 SQL 陳述式，**其中**子句會限制的選取項目。  
  
 建構物件之後但在您呼叫之前，您必須建立資料錄集物件的篩選條件及其**開啟**成員函式 (或在呼叫之前**Requery**現有的資料錄集的成員函式物件，其**開啟**先前呼叫成員函式)。  
  
#### <a name="to-specify-a-filter-for-a-recordset-object"></a>若要指定的篩選資料錄集物件  
  
1.  建構一個新的資料錄集物件 (或準備呼叫**Requery**現有的物件)。  
  
2.  設定物件的值[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)資料成員。  
  
     篩選器是以 null 結束的字串，包含內容的 SQL**其中**子句，但不是關鍵字**其中**。 例如，使用：  
  
    ```  
    m_pSet->m_strFilter = "CourseID = 'MATH101'";  
    ```  
  
     not  
  
    ```  
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";  
    ```  
  
    > [!NOTE]
    >  常值字串"MATH101"會以單引號上方顯示。 在 ODBC SQL 規格中，單引號用來表示字元字串常值。 請檢查您的 ODBC 驅動程式文件，您在此情況下的 DBMS 引號需求。 這個語法也會討論進一步接近本主題的結尾。  
  
3.  設定需要例如排序次序、 鎖定模式或參數的其他選項。 指定的參數會特別有用。 參數化篩選的相關資訊，請參閱[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
4.  呼叫**開啟**新物件 (或**Requery**先前開啟的物件)。  
  
> [!TIP]
>  在您的篩選條件中使用參數可能是最有效率的擷取記錄的方式。  
  
> [!TIP]
>  資料錄集篩選器可用於[聯結](../../data/odbc/recordset-performing-a-join-odbc.md)資料表以及使用[參數](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)取得，或在執行階段計算資訊為基礎。  
  
 資料錄集選取只在符合您指定的搜尋條件的記錄。 例如，若要指定課程篩選上面所述 (假設變數`strCourseID`目前設定，例如，"MATH101")，執行下列動作：  
  
```  
// Using the recordset pointed to by m_pSet  
  
// Set the filter  
m_pSet->m_strFilter = "CourseID = " + strCourseID;   
  
// Run the query with the filter in place  
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )  
  
// Use the recordset  
```  
  
 資料錄集包含 MATH101 記錄類別的所有章節。  
  
 請注意在上述範例使用字串變數如何設定篩選字串。 這是典型的用法。 但假設您想要指定常值 100 課程識別碼。 下列程式碼會示範如何設定正確包含常值的篩選字串：  
  
```  
m_strFilter = "StudentID = '100'";   // correct  
```  
  
 請注意使用單引號字元。如果您直接設定篩選字串，此篩選條件字串是**不**:  
  
```  
m_strFilter = "StudentID = 100";   // incorrect for some drivers  
```  
  
 用引號括住如上所示符合 ODBC 規格中，但某些 Dbms 可能需要其他的引號字元。 如需詳細資訊，請參閱[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
> [!NOTE]
>  如果您選擇覆寫資料錄集的預設 SQL 字串傳遞您自己的 SQL 字串**開啟**，您不應將篩選條件，如果您的自訂字串具有**其中**子句。 如需覆寫預設 SQL 的詳細資訊，請參閱[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)   
 [資料錄集： 資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)