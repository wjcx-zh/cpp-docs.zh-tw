---
title: 資料錄集： 篩選資料錄 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5feb97d2bf3cbd3787ed2253b3b2dd4a257b5315
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040787"
---
# <a name="recordset-filtering-records-odbc"></a>資料錄集：篩選資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。  
  
本主題說明如何篩選資料錄集，使其選取可用的資料錄對特定子集。 比方說，您可以選取只針對特定的課程，例如 MATH101 的類別區段。 篩選條件是由 SQL 的內容定義的搜尋條件**其中**子句。 此架構將它附加到資料錄集的 SQL 陳述式中，當**其中**子句限制選取項目。  
  
建構物件之後但在您呼叫之前，您必須建立將資料錄集物件的篩選條件及其`Open`成員函式 (或在呼叫之前`Requery`成員函式，以現有的資料錄集物件，其`Open`成員函式具有先前已呼叫）。  
  
#### <a name="to-specify-a-filter-for-a-recordset-object"></a>若要指定的資料錄集物件的篩選器  
  
1. 建構新的資料錄集物件 (或準備呼叫`Requery`現有的物件)。  
  
1. 設定物件的值[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)資料成員。  
  
     篩選器是以 null 結尾的字串，包含 SQL 的內容**何處**子句，但不是關鍵字**其中**。 例如，使用：  
  
    ```  
    m_pSet->m_strFilter = "CourseID = 'MATH101'";  
    ```  
  
     not  
  
    ```  
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";  
    ```  
  
    > [!NOTE]
    >  常值字串"MATH101 」 會顯示與上述的單一引號括起來。 在 ODBC SQL 規格中，單引號用來表示字元字串常值。 請檢查您在此情況下 DBMS 引號需求 」 的 ODBC 驅動程式文件。 此語法也會討論進一步接近本主題的結尾。  
  
1. 設定您需要例如排序、 鎖定的模式或參數的其他任何選項。 指定的參數就特別有用。 如需參數化篩選的資訊，請參閱[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
1. 呼叫`Open`新的物件 (或`Requery`先前開啟的物件)。  
  
> [!TIP]
>  在您的篩選條件中使用參數可能是最有效率的方法來擷取記錄。  
  
> [!TIP]
>  資料錄集篩選器可用於[聯結](../../data/odbc/recordset-performing-a-join-odbc.md)資料表，而用於[參數](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)根據取得，或在執行階段計算的資訊。  
  
資料錄集選取只在符合您所指定的搜尋條件的記錄。 例如，若要指定課程篩選上面所述 (假設變數`strCourseID`目前設定，例如，為 「 MATH101")，執行下列動作：  
  
```  
// Using the recordset pointed to by m_pSet  
  
// Set the filter  
m_pSet->m_strFilter = "CourseID = " + strCourseID;   
  
// Run the query with the filter in place  
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )  
  
// Use the recordset  
```  
  
資料錄集包含 MATH101 記錄所有的類別區段。  
  
請注意如何在範例中，使用字串變數設定的篩選條件字串。 這是典型的用法。 但假設您想要指定常值 100 做為課程識別碼。 下列程式碼示範如何設定正確包含常值的篩選字串：  
  
```  
m_strFilter = "StudentID = '100'";   // correct  
```  
  
請注意，使用單引號字元字串;您可以直接設定篩選條件字串，篩選條件字串是否**不**:  
  
```  
m_strFilter = "StudentID = 100";   // incorrect for some drivers  
```  
  
如上所示的引用符合 ODBC 規格中，但某些 Dbms 可能需要其他的引號字元。 如需詳細資訊，請參閱 < [SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
> [!NOTE]
>  如果您選擇覆寫資料錄集的預設 SQL 字串，傳遞您自己的 SQL 字串`Open`，您不應將篩選條件，如果您的自訂字串已**其中**子句。 如需有關如何覆寫預設 SQL 的詳細資訊，請參閱[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[資料錄集：資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)