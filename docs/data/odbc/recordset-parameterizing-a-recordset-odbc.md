---
title: 資料錄集： 參數化資料錄集 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 275cd9d2ee7ccbd4c9972c00ae6fbb8f33166a0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098546"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>資料錄集：參數化資料錄集 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 有時候您可能想要能夠在執行階段中，選取記錄使用導出或從您的終端使用者取得的資訊。 資料錄集參數可讓您達成這個目的。  
  
 本主題說明：  
  
-   [參數化資料錄集的用途](#_core_parameterized_recordsets)。  
  
-   [時間和原因可能會想要參數化資料錄集](#_core_when_to_use_parameters)。  
  
-   [如何宣告參數資料成員中資料錄集類別](#_core_parameterizing_your_recordset_class)。  
  
-   [如何在執行階段傳遞給資料錄集物件的參數資訊](#_core_passing_parameter_values_at_run_time)。  
  
##  <a name="_core_parameterized_recordsets"></a> 參數化資料錄集  
 參數化資料錄集可讓您傳遞參數在執行階段的資訊。 這會有兩個重要的影響：  
  
-   它可能會導致更好的執行速度。  
  
-   它可讓您建立查詢，在執行階段，根據在設計階段，您無法使用的資訊，例如取自使用者資訊，或在執行階段計算。  
  
 當您呼叫**開啟**來執行查詢時，資料錄集使用的參數資訊以完成其**SQL SELECT**陳述式。 您可以參數化的任何資料錄集。  
  
##  <a name="_core_when_to_use_parameters"></a> 使用參數的時機  
 參數的一般用法包括：  
  
-   執行階段引數傳遞給預先定義的查詢。  
  
     若要將參數傳遞給預存程序，您必須指定完整的自訂 ODBC**呼叫**陳述式，使用參數替代符號，當您呼叫**開啟**，覆寫資料錄集的預設 SQL 陳述式。 如需詳細資訊，請參閱[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)中*類別庫參考*和[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)和[資料錄集： 宣告預先定義的查詢 (ODBC) 的類別](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。  

  
-   有效率地執行不同的參數資訊的許多種需求。  
  
     比方說，每次使用者查詢資訊的特定學生在學生系統註冊資料庫，您可以指定學生的名稱或識別碼做為參數，從使用者取得。 然後，當您呼叫資料錄集的**Requery**成員函式，查詢會選取只該學生的記錄。  
  
     資料錄集的篩選條件字串，儲存在**m_strFilter**，可能看起來像這樣：  
  
    ```  
    "StudentID = ?"  
    ```  
  
     假設您取得變數中的學生識別碼`strInputID`。 當您將參數設`strInputID`（例如學生識別碼為 100） 變數的值會繫結至所代表的參數預留位置"？"中的篩選條件字串。  
  
     指定參數值，如下所示：  
  
    ```  
    strInputID = "100";  
    ...  
    m_strParam = strInputID;  
    ```  
  
     您不想在這種方式設定篩選字串：  
  
    ```  
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted  
                                       // for some drivers  
    ```  
  
     如需如何正確使用篩選字串的引號的討論，請參閱[資料錄集： 篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
     參數值每次都會不同您新的學生識別碼重新查詢資料錄集  
  
    > [!TIP]
    >  使用參數是比只是篩選器更有效率。 參數化資料錄集，資料庫必須處理 SQL**選取**陳述式一次。 以不含參數，已篩選資料錄集**選取**必須處理陳述式每次您**Requery**以新的篩選值。  
  
 如需篩選器的詳細資訊，請參閱[資料錄集： 篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
##  <a name="_core_parameterizing_your_recordset_class"></a> 參數化資料錄集類別  
  
> [!NOTE]
>  本節適用於衍生自物件`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，實作參數是類似的程序。 如需詳細資訊，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 建立資料錄集類別之前，請判斷您需要哪些參數、 其資料類型為何，和資料錄集如何使用它們。  
  
#### <a name="to-parameterize-a-recordset-class"></a>參數化資料錄集類別  
  
1.  執行[MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)從**加入類別**建立類別。  
  
2.  指定資料錄集的資料行的欄位資料成員。  
  
3.  精靈會寫入您的專案中的檔案中的類別之後，請移至的.h 檔案，並以手動方式將一或多個參數的資料成員加入至類別宣告。 新增看起來類似下列的範例、 快照集類別的部分設計來回答查詢 」 中有哪些學生資深類別嗎？ 」  
  
    ```  
    class CStudentSet : public CRecordset  
    {  
    // Field/Param Data  
        CString m_strFirstName;  
        CString m_strLastName;  
        CString m_strStudentID;  
        CString m_strGradYear;  
  
        CString m_strGradYrParam;  
    };  
    ```  
  
     在精靈產生的欄位資料成員之後加入您的參數資料成員。 慣例是 「 文字"Param"附加至每個使用者定義的參數名稱。  
  
4.  修改[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)在.cpp 檔案中的成員函式定義。 每個參數資料成員加入至類別中加入 RFX 函式呼叫。 如需撰寫 RFX 函式的詳細資訊，請參閱[資料錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 之前參數的單一呼叫 RFX 呼叫：  
  
    ```  
    pFX->SetFieldType( CFieldExchange::param );  
    // RFX calls for parameter data members  
    ```  
  
5.  資料錄集類別的建構函式中遞增的參數計數`m_nParams`。  
  
     如需資訊，請參閱[資料錄欄位交換： 精靈程式碼的使用](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)。  
  
6.  當您撰寫程式碼會建立此類別的資料錄集物件時，將"？"（問號） 在您的 SQL 陳述式字串中每個位置是要被取代之參數的符號。  
  
     在執行階段，「？ 」 填入預留位置，順序，在您傳遞的參數值。 之後的第一個參數的資料成員設定[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)呼叫取代第一個"？"SQL 字串中的第二個參數的資料成員會取代第二個"？"，依此類推。  
  
> [!NOTE]
>  參數的順序很重要： RFX 的順序呼叫中的參數您`DoFieldExchange`函式必須符合 SQL 字串中參數預留位置的順序。  
  
> [!TIP]

>  若要使用最可能的字串是您指定的字串 （如果有的話） 的類別[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)資料成員，但有些 ODBC 驅動程式可以讓參數中的其他 SQL 子句。  
  
##  <a name="_core_passing_parameter_values_at_run_time"></a> 在執行階段傳遞參數值  
 您必須指定參數值，才能呼叫**開啟**（適用於新的資料錄集物件） 或**Requery** （適用於現有的我的最愛）。  
  
#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>將參數值傳遞至資料錄集物件，在執行階段  
  
1.  建構資料錄集物件。  
  
2.  準備字串或字串，例如**m_strFilter**包含 SQL 陳述式或它的組件的字串。 將"？"預留位置的參數資訊的地方。  
  
3.  執行階段參數將值指派給物件的每個參數的資料成員。  
  
4.  呼叫**開啟**成員函式 (或**Requery**，以現有的資料錄集)。  
  
 例如，假設您想要指定使用在執行階段取得的資訊資料錄集的篩選字串。 假設您已建構類別的資料錄集`CStudentSet`稍早 — 呼叫`rsStudents`，而現在想要重新查詢會針對特定種類的學生資訊。  
  
```  
// Set up a filter string with   
// parameter placeholders  
rsStudents.m_strFilter = "GradYear <= ?";  
  
// Obtain or calculate parameter values   
// to pass--simply assigned here   
CString strGradYear = GetCurrentAcademicYear( );  
  
// Assign the values to parameter data members  
rsStudents.m_strGradYrParam = strGradYear;  
  
// Run the query  
if( !rsStudents.Requery( ) )  
    return FALSE;  
```  
  
 資料錄集包含這些學生的記錄符合篩選器，所建構執行階段參數所指定的條件。 在此情況下，資料錄集包含所有資深學生。  
  
> [!NOTE]
>  如有需要您可以設定參數的資料成員的值為 Null，使用[SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull)。 您同樣可以檢查參數資料成員是否為 Null，使用[IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull)。  
  
## <a name="see-also"></a>另請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 加入、 更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)