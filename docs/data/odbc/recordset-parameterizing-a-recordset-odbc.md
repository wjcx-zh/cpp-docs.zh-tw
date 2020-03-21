---
title: 資料錄集：參數化資料錄集 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: eaf95312b73b5165d64de7f9ded95db29d8909d0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075810"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>資料錄集：參數化資料錄集 (ODBC)

本主題適用於 MFC ODBC 類別。

有時您可能會想要使用您所計算出來或從使用者取得的資訊，在執行階段選取資料錄。 資料錄集參數可讓您達成該目標。

本主題將說明：

- [參數化資料錄集的目的](#_core_parameterized_recordsets)。

- [您可能會想要參數化資料錄集的時機和原因](#_core_when_to_use_parameters)。

- [如何在您的資料錄集類別中宣告參數資料成員](#_core_parameterizing_your_recordset_class)。

- [如何在執行階段將參數資訊傳遞至資料錄集物件](#_core_passing_parameter_values_at_run_time)。

##  <a name="parameterized-recordsets"></a><a name="_core_parameterized_recordsets"></a> 參數化的資料錄集

參數化的資料錄集可讓您在執行階段傳遞參數資訊。 這能提供兩個重要的效果：

- 它可能可以帶來更佳的執行速度。

- 它能讓您根據在設計階段無法取得的資訊在執行階段建置查詢，例如在執行階段從使用者取得或計算出來的資訊。

當您呼叫 `Open` 來執行查詢時，資料錄集會使用參數資訊來完成其 **SQL SELECT** 陳述式。 您可以參數化任何資料錄集。

##  <a name="when-to-use-parameters"></a><a name="_core_when_to_use_parameters"></a> 使用參數的時機

參數的典型用途包括：

- 將執行階段引數傳遞至預先定義的查詢。

   若要將參數傳遞至預存程序，您必須在呼叫 `Open` 時指定完整的自訂 ODBC **CALL** 陳述式 (搭配參數預留位置)，並覆寫資料錄集的預設 SQL 陳述式。 如需詳細資訊，請參閱《類別程式庫參考》中的 [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) 及 [SQL：自訂資料錄集的 SQL 陳述式 (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) 和[資料錄集：宣告預先定義查詢的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。

- 搭配不同的參數資訊有效執行數個重新查詢。

   例如，每當您的使用者在學生註冊資料庫中查詢特定學生的資訊時，您可以將該學生的姓名或識別碼指定為從該使用者取得的參數。 接著，當您呼叫資料錄集的 `Requery` 成員函式時，查詢便只會選取該學生的記錄。

   您的資料錄集篩選字串 (儲存在 `m_strFilter` 中) 看起來可能會像這樣：

    ```cpp
    "StudentID = ?"
    ```

   假設您是在變數 `strInputID`中取得學生識別碼。 當您將參數設定為 `strInputID` (例如學生識別碼 100) 時，變數的值會繫結至在篩選字串中由 "?" 所代表的參數預留位置。

   指派參數值，如下所示：

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   您不應該以下列方式設定篩選字串：

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   如需針對篩選字串正確使用引號的討論，請參閱[資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。

   每當您針對新的學生識別碼重新查詢資料錄集時，參數值都會不同。

   > [!TIP]
   > 使用參數比起單純使用篩選還要更有效率。 針對參數化的資料錄集，資料庫只能單次處理 SQL **SELECT** 陳述式。 針對沒有參數的已篩選資料錄集，在您每次搭配新的篩選值進行 `Requery` 時，都必須處理 **SELECT** 陳述式。

如需篩選的詳細資訊，請參閱[資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。

##  <a name="parameterizing-your-recordset-class"></a><a name="_core_parameterizing_your_recordset_class"></a> 參數化您的資料錄集類別

> [!NOTE]
> 本節適用於衍生自 `CRecordset` 的物件，其中尚未實作大量資料列擷取。 如果您正在使用大量資料列擷取，其實作參數的程序也相當類似。 如需詳細資訊，請參閱[資料錄集：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

在您建立資料錄集類別之前，請先判斷所需的參數、其資料類型，以及資料錄集使用它們的方式。

#### <a name="to-parameterize-a-recordset-class"></a>參數化資料錄集類別

> [!NOTE]
> Visual Studio 2019 和更新版本中未提供 MFC ODBC 消費者精靈。 您仍然可以手動建立此功能。

1. 從 [新增類別] 執行 [MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)來建立該類別。

1. 針對資料錄集的資料行指定欄位資料成員。

1. 在精靈將類別寫入您專案中的檔案後，請移至 .h 檔案並手動將一或多個參數資料成員加入類別宣告。 結果看起來可能會類似下列範例，其為設計來回答查詢「有哪些學生屬於高年級班級？」之快照集類別的一部分。

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

   將您的參數資料成員加入至由精靈產生之欄位資料成員的後方。 慣例是將文字 "Param" 附加至每個使用者定義的參數名稱。

1. 修改 .cpp 檔案中的 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 成員函式定義。 針對每個您加入類別的參數資料成員加入 RFX 函式呼叫。 如需撰寫 RFX 函式的相關資訊，請參閱[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 在進行對參數的 RFX 呼叫之前，先針對下列項目進行單一呼叫：

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. 在您資料錄集類別的建構函式中累加參數的計數，`m_nParams`。

   如需詳細資訊，請參閱[資料錄欄位交換：使用精靈程式碼](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md)。

1. 當您撰寫會建立此類別之資料錄集物件的程式碼時，請在 SQL 陳述式字串中會取代參數的每個位置放置 "?" (問號) 符號。

   在執行階段時，"?" 預留位置會依序被您所傳遞的參數值填入。 在 [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) 呼叫後所設定的第一個參數資料成員將會取代 SQL 字串中的第一個 "?"，而第二個參數資料成員則會取代第二個 "?"，依此類推。

> [!NOTE]
> 參數順序很重要：針對您 `DoFieldExchange` 函式中參數的 RFX 呼叫順序，必須符合您 SQL 字串中參數預留位置的順序。

> [!TIP]
> 最可能搭配使用的字串，是您針對類別的 [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) 資料成員所指定的字串 (若有的話)，但某些 ODBC 驅動程式可能會允許其他 SQL 子句中的參數。

##  <a name="passing-parameter-values-at-run-time"></a><a name="_core_passing_parameter_values_at_run_time"></a> 在執行階段傳遞參數值

您必須在呼叫 `Open` (針對新的資料錄集物件) 或 `Requery` (針對現有資料錄集物件) 之前指定參數值。

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>在執行階段將參數值傳遞至資料錄集物件

1. 建構資料錄集物件。

1. 準備包含 SQL 陳述式 (或部分陳述式) 的字串，例如 `m_strFilter` 字串。 將 "?" 預留位置置於要填入參數資訊的位置。

1. 將執行階段參數值指派至物件的每個參數資料成員。

1. 呼叫 `Open` 成員函式 (針對現有的資料錄集則是 `Requery`)。

例如，假設您想要使用在執行階段取得的資訊，為您的資料錄集指定篩選字串。 假設您已預先建構類別 `CStudentSet` 的資料錄集 (稱為 `rsStudents`)，且現在想要重新查詢它以取得特定類型的學生資訊。

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

資料錄集包含其記錄符合由篩選所指定條件之學生的記錄，該篩選是根據執行階段參數所建構。 在此情況下，資料錄集會包含所有高年級學生的記錄。

> [!NOTE]
>  若有需要，您可以使用 [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull) 將參數資料成員的值設為 Null。 您也可以使用 [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) 來檢查是否有參數資料成員為 Null。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：新增、更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)