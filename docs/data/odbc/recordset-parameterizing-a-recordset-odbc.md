---
title: 資料錄集：參數化資料錄集 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: f58a33a0c43cb0d70d98f3f2ae33f766058b1c23
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331265"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>資料錄集：參數化資料錄集 (ODBC)

本主題適用於 MFC ODBC 類別。

有時候您可能想要能夠在執行階段中，選取記錄使用您已從計算或取得您的終端使用者的資訊。 資料錄集參數可讓您達成這個目標。

本主題說明：

- [參數化資料錄集的目的](#_core_parameterized_recordsets)。

- [何時及為何您可能想要參數化資料錄集](#_core_when_to_use_parameters)。

- [如何宣告參數資料錄集類別中的資料成員](#_core_parameterizing_your_recordset_class)。

- [如何將參數資訊傳遞至資料錄集物件，在執行階段](#_core_passing_parameter_values_at_run_time)。

##  <a name="_core_parameterized_recordsets"></a> 參數化資料錄集

參數化資料錄集可讓您將在執行階段的參數資訊傳遞。 這有兩個重要的效果：

- 它可能會導致更好的執行速度。

- 它可讓您建立查詢在執行階段，根據在設計階段，您無法使用的資訊，例如資訊會取自您的使用者，或在執行階段計算。

當您呼叫`Open`若要執行查詢，資料錄集使用的參數資訊以完成其**SQL SELECT**陳述式。 您可以參數化的任何資料錄集。

##  <a name="_core_when_to_use_parameters"></a> 使用參數的時機

參數的典型用途包括：

- 執行階段引數傳遞給預先定義的查詢。

   若要將參數傳遞給預存程序，您必須指定完整的自訂 ODBC**呼叫**陳述式，使用參數替代符號，當您呼叫`Open`，覆寫資料錄集的預設 SQL 陳述式。 如需詳細資訊，請參閱 < [crecordset:: Open](../../mfc/reference/crecordset-class.md#open)中*類別庫參考*並[SQL： 自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)並[資料錄集： 宣告預先定義的查詢 (ODBC) 的類別](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。

- 有效率地執行不同的參數資訊的許多種需求。

   比方說，每次您的使用者查詢資訊的特定學生在學生註冊資料庫中，您可以指定學生的名稱或識別碼當做參數，從使用者處取得。 然後，當您呼叫資料錄集的`Requery`成員函式，查詢會選取只該學生的記錄。

   資料錄集的篩選條件字串，儲存在`m_strFilter`，可能會看起來像這樣：

    ```cpp
    "StudentID = ?"
    ```

   假設您取得在變數中的學生識別碼`strInputID`。 當您將參數設定為`strInputID`（例如，學生識別碼為 100） 變數的值繫結至所代表的參數預留位置"？"中的篩選條件字串。

   參數值的指派，如下所示：

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   您不想在這種方式設定的篩選字串：

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   如需如何正確使用引號括住，來篩選字串的討論，請參閱[資料錄集： 篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。

   參數為不同的值每次您重新資料錄集查詢新的學生識別碼。

   > [!TIP]
   > 使用參數是比只是篩選器更有效率。 以參數化資料錄集，資料庫必須處理 SQL**選取**陳述式一次。 已篩選的資料錄集，如果沒有參數，如**選取 **必須處理陳述式每次您`Requery`使用新的篩選值。

如需有關篩選的詳細資訊，請參閱[資料錄集： 篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。

##  <a name="_core_parameterizing_your_recordset_class"></a> 參數化資料錄集類別

> [!NOTE]
> 本節適用於物件衍生自`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，實作參數是類似的程序。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

建立您的資料錄集類別之前，請決定您需要哪些參數，其資料類型為何，以及資料錄集如何使用它們。

#### <a name="to-parameterize-a-recordset-class"></a>將參數化資料錄集類別

1. 執行[MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)從**加入類別**建立類別。

1. 指定資料錄集的資料行的欄位資料成員。

1. 精靈會寫入您的專案中的檔案中的類別之後，請移至的.h 檔案，並以手動方式將一或多個參數資料成員新增至類別宣告。 新增可能看起來如下列範例所示，快照集類別的部分設計來回答查詢 」 中有哪些學生資深類別嗎？ 」

    ```cpp
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

   在精靈產生的欄位資料成員之後加入參數資料成員。 慣例是將"Param"這個字附加至每個使用者定義的參數名稱。

1. 修改[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)在.cpp 檔案中的成員函式定義。 每個參數的資料成員新增至類別中新增的 RFX 函式呼叫。 如需撰寫 RFX 函式的詳細資訊，請參閱 <<c0> [ 資料錄欄位交換： RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 之前的單一呼叫 RFX 呼叫的參數：

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. 在您的資料錄集類別的建構函式，累加計數的參數， `m_nParams`。

   如需資訊，請參閱[資料錄欄位交換： 精靈程式碼的使用](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)。

1. 當您撰寫的程式碼，建立這個類別的資料錄集物件時，將"？"在您的 SQL 陳述式字串中每個位置是要取代之參數 （問號） 符號。

   在執行階段，"？"預留位置會填入，順序，則會在您傳遞的參數值。 之後的第一個參數的資料成員設定[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)呼叫取代第一個"？"在 SQL 字串中，第二個參數的資料成員會取代第二個"？"，依此類推。

> [!NOTE]
> 參數的順序很重要： RFX 的順序呼叫中參數的您`DoFieldExchange`函式必須符合 SQL 字串中參數預留位置的順序。

> [!TIP]
> 使用最可能的字串是您指定的字串 （如果有的話） 的類別[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)資料成員，但有些 ODBC 驅動程式可能會允許其他 SQL 子句中的參數。

##  <a name="_core_passing_parameter_values_at_run_time"></a> 在執行階段傳遞參數值

您必須指定參數值，然後再呼叫`Open`（適用於新的資料錄集物件） 或`Requery`（適用於現有的帳戶）。

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>若要將資料錄集物件中的參數值，在執行階段

1. 建構資料錄集物件。

1. 準備一個字串或字串，例如`m_strFilter`包含 SQL 陳述式或其一部分的字串。 將"？"預留位置的參數資訊的地方。

1. 執行階段參數將值指派給物件的每個參數的資料成員。

1. 呼叫`Open`成員函式 (或`Requery`，為現有的資料錄集)。

例如，假設您想要指定使用在執行階段取得的資訊資料錄集的篩選字串。 假設您已建構類別的資料錄集`CStudentSet`稍早，稱為`rsStudents`— 而現在想要針對特定種類的學生資訊重新查詢。

```cpp
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

資料錄集包含這些學生記錄符合篩選器，從執行階段參數的建構所指定的條件。 在此情況下，資料錄集可包含的所有資深學生的記錄。

> [!NOTE]
>  如有需要您可以設定參數的資料成員的值為 Null，使用[SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull)。 您同樣可以檢查參數資料成員是否為 Null，使用[IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：新增、更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)