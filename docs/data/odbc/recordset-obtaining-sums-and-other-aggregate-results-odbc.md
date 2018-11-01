---
title: 資料錄集：取得 SUM 和其他彙總結果 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
ms.openlocfilehash: 7a63e6b0e4ac26fb2806d8505e3fcd8f5daf0f10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491577"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>資料錄集：取得 SUM 和其他彙總結果 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題說明如何取得彙總的結果，使用下列[SQL](../../data/odbc/sql.md)關鍵字：

- **總和**具有數值資料類型會計算資料行中值的總計。

- **最小**具有數值資料類型中擷取資料行中的最小值。

- **最大**具有數值資料類型中擷取資料行中的最大值。

- **AVG**計算平均值的資料行中的所有值具有數值資料類型。

- **計數**計算任何資料類型的資料行中的記錄數目。

若要取得有關資料來源中之記錄的統計資訊而不是從資料來源擷取記錄，您可以使用這些 SQL 函式。 資料錄集，通常會建立包含單一記錄 （如果所有資料行彙總），會包含值。 (可能有多筆記錄如果您使用**GROUP BY**子句。)這個值會計算或執行 SQL 函式所擷取的結果。

> [!TIP]
>  若要將 SQL **GROUP BY**子句 (而且可能**HAVING**子句) 到您的 SQL 陳述式，將它附加至結尾`m_strFilter`。 例如: 

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

您可以限制您使用的篩選和排序資料行取得彙總結果的記錄數目。

> [!CAUTION]
>  某些彙總運算子會傳回不同的資料類型，從彙總的資料行。

- **總和**和**AVG**可能會傳回下一個較大的資料類型 (例如，呼叫`int`傳回**長**或**double**)。

- **計數**通常會傳回**長**不論目標資料行類型。

- **最大**並**MIN**傳回相同的資料類型，這些計算的資料行。

     例如，**加入類別**精靈會建立`long``m_lSales`適應 Sales 資料行，但您需要將此取代為`double m_dblSumSales`適應彙總結果的資料成員。 請參閱下列範例。

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>若要取得資料錄集的彙總結果

1. 建立資料錄集，如中所述[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)包含您要取得彙總結果的資料行。

1. 修改[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)函式資料錄集。 取代字串，表示資料行名稱 (第二個引數[RFX](../../data/odbc/record-field-exchange-using-rfx.md)函式呼叫) 表示的資料行的彙總函式的字串。 比方說，程式碼取代：

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     取代為：

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. 開啟資料錄集。 彙總作業的結果會留在`m_dblSumSales`。

> [!NOTE]
>  精靈會實際指派沒有 Hungarian 前置詞的資料成員名稱。 比方說，精靈會產生`m_Sales`Sales 資料行，而非`m_lSales`稍早用於圖例的名稱。

如果您使用[CRecordView](../../mfc/reference/crecordview-class.md)檢視資料類別中，您必須變更 DDX 函式呼叫，以顯示新的資料成員值; 在此情況下，將它從變更：

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

收件者:

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)