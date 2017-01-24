---
title: "資料錄集：參數化資料錄集 (ODBC) | Microsoft Docs"
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
  - "ODBC 資料錄集, 參數化"
  - "參數化資料錄集"
  - "傳遞參數, 在執行階段時至查詢"
  - "資料錄集, 參數化"
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：參數化資料錄集 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 有時您可能想要使用計算出來或從使用者處取得的資訊，在執行階段時選取資料錄。  您可以使用資料錄集的參數達成這個目的。  
  
 這個主題說明：  
  
-   [參數型資料錄集的目的](#_core_parameterized_recordsets)。  
  
-   [參數化資料錄集的時機和原因](#_core_when_to_use_parameters)。  
  
-   [資料錄集類別的參數資料成員的宣告方法](#_core_parameterizing_your_recordset_class)。  
  
-   [在 Run Time 將參數資訊傳遞至資料錄集物件的方法](#_core_passing_parameter_values_at_run_time)。  
  
##  <a name="_core_parameterized_recordsets"></a> 參數型資料錄集  
 參數型資料錄集讓您可以在執行階段中傳遞參數。  這點帶來兩項有意義的影響：  
  
-   這可能會產生更快的執行速度。  
  
-   讓您在執行階段時，根據在設計階段無法取得的資訊 \(例如自您的使用者處取得或是在 Run Time 中計算所得的資訊\) 建置一個查詢。  
  
 當您呼叫 **Open** 來執行查詢時，資料錄集會使用參數資訊來完成它的 **SQL SELECT** 陳述式。  您可以參數化任何資料錄集。  
  
##  <a name="_core_when_to_use_parameters"></a> 參數使用時機  
 參數的一般用法包括：  
  
-   傳遞執行階段引數至預先定義的查詢。  
  
     若要將參數傳遞至預存程序，您必須指定一個完整的自訂 ODBC **CALL** 陳述式 ─ 使用參數替代符號 ─ 當您在呼叫 **Open** 以覆寫資料錄集的預設 SQL 陳述式時。  如需詳細資訊，請參閱《類別庫參考》中的 [CRecordset::Open](../Topic/CRecordset::Open.md) 以及 [SQL：自訂資料錄集的 SQL 陳述式 \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md) 和[資料錄集：宣告預先定義查詢的類別 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。  
  
-   有效率地以不同的參數資訊來執行許多種需求。  
  
     例如，每當您的使用者在查詢學生註冊資料庫的特定學生資訊時，您可指定學生姓名或 ID 當做從使用者處取得的參數。  接著當您呼叫資料錄集的 **Requery** 成員函式時，查詢只會選取該學生的資料錄。  
  
     儲存於 **m\_strFilter** 內的資料錄集篩選字串看起來可能像這樣：  
  
    ```  
    "StudentID = ?"  
    ```  
  
     假設您取得在 `strInputID` 變數內的學生 ID。  則當您設定參數為 `strInputID` 時 \(例如，學生 ID 100\)，變數值便會繫結至篩選字串中以 "?" 表示的參數替代符號 \(Placeholder\)。  
  
     依照下列方式指定參數值：  
  
    ```  
    strInputID = "100";  
    ...  
    m_strParam = strInputID;  
    ```  
  
     您不會想要以這種方式設定篩選條件字串：  
  
    ```  
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted  
                                       // for some drivers  
    ```  
  
     如需如何在篩選字串中正確使用引號的詳細討論，請參閱[資料錄集：篩選資料錄 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
     每次您在重新查詢資料錄集的新學生 ID 時所使用的參數值都會不一樣。  
  
    > [!TIP]
    >  使用參數比只用篩選條件還要更有效率。  針對一個參數型資料錄集，資料庫只處理 SQL **SELECT** 陳述式一次。  針對不含參數的篩選型資料錄集，**SELECT** 陳述式會在每次您以一個新的篩選值 **Requery** 時進行處理。  
  
 如需篩選條件的詳細資訊，請參閱[資料錄：篩選資料錄 \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
##  <a name="_core_parameterizing_your_recordset_class"></a> 參數化資料錄集類別  
  
> [!NOTE]
>  本章節適用於尚未實作大量資料列擷取的 `CRecordset` 衍生物件。  若您正在使用大量資料列擷取，實作參數是一個類似的處理程序。  如需詳細資訊，請參閱文件[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 在建立您的資料錄集類別之前，請先決定您所需要的參數、參數的資料型別和資料錄集使用參數的方式。  
  
#### 若要參數化資料錄集類別  
  
1.  執行 \[加入類別\] 的 [MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)以建立類別。  
  
2.  指定資料錄集資料行的欄位資料成員。  
  
3.  在精靈於專案中的檔案編寫類別之後，請到 .h 的檔案中，並手動在類別宣告中加入一或多個參數資料成員。  所加入程式碼看起來會像下列範例所示，快照集類別的部分是設計來回答「哪些學生在高年級班級？」的查詢。  
  
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
  
     在精靈所產生的欄位資料成員後面加入您的參數資料成員。  加入慣例是將 "Param" 文字附加至每個使用者定義的參數名稱。  
  
4.  修改 .CPP 檔案內的 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 成員函式定義。  為每個您加到類別內的參數資料成員加入一個 RFX 函式呼叫 \(Function Call\)。  如需撰寫 RFX 函式的詳細資訊，請參閱[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。  在參數的 RFX 呼叫之前有一個單一呼叫：  
  
    ```  
    pFX->SetFieldType( CFieldExchange::param );  
    // RFX calls for parameter data members  
    ```  
  
5.  在您的資料錄集類別中的建構函式，將參數總數增加至 `m_nParams`。  
  
     如需詳細資訊，請參閱[資料錄欄位交換：精靈程式碼的使用](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)。  
  
6.  當您在撰寫用來建立這個類別的資料錄集物件的程式碼時，請在 SQL 陳述式字串中要取代參數的每個地方放置問號符號。  
  
     在執行階段時，"?" 替代符號會依序填入您傳遞的參數值。  在 [SetFieldType](../Topic/CFieldExchange::SetFieldType.md) 呼叫後的第一個參數資料成員集會取代 SQL 字串內的第一個 "?"，第二個參數資料成員會取代第二個 "?" 等等。  
  
> [!NOTE]
>  參數的順序很重要：您的 `DoFieldExchange` 函式內參數的 RFX 呼叫順序必須符合在 SQL 字串中的參數替代符號順序。  
  
> [!TIP]
>  最可能使用的字串是您為類別的 [m\_strFilter](../Topic/CRecordset::m_strFilter.md) 資料成員所指定 \(若有的話\) 的字串，但某些 ODBC 驅動程式可能允許在其他 SQL 子句中有參數。  
  
##  <a name="_core_passing_parameter_values_at_run_time"></a> 在執行階段傳遞參數值  
 您必須在呼叫 **Open** \(針對新資料錄集物件\) 或 **Requery** \(針對現有資料錄集物件\) 前先指定參數值。  
  
#### 若要在執行階段將參數值傳遞至資料錄集物件  
  
1.  建構資料錄集物件。  
  
2.  準備一個字串或一群字串，例如 **m\_strFilter** 字串，此字串包含 SQL 陳述式，或部分的陳述式。  在接收參數資訊的地方放置一個 "?" 替代符號。  
  
3.  為物件的每個參數資料成員設定執行階段參數值。  
  
4.  呼叫 **Open** 成員函式 \(對現有資料錄集則是呼叫 **Requery**\)。  
  
 例如，假設您想要為使用執行階段取得的資訊之資料錄集，指定一個篩選字串。  假設您先前已建構了 `CStudentSet` 類別的資料錄集 \(稱為 `rsStudent`\)，而現在想要重新查詢以便取得特定類型的學生資訊。  
  
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
  
 該資料錄集會包含那些資料錄符合篩選所指定條件的學生資料錄 \(篩選是用執行階段參數所建構\)。  在這個案例中，資料錄集包含所有高年級學生的資料錄。  
  
> [!NOTE]
>  如有需要，您可使用 [SetParamNull](../Topic/CRecordset::SetParamNull.md) 將參數資料成員值設定為 Null。  同樣地，您可使用 [IsFieldNull](../Topic/CRecordset::IsFieldNull.md) 來檢查參數資料成員是否為 Null。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：加入、更新和刪除資料錄 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [資料錄集：資料錄集選取資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)