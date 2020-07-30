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
ms.openlocfilehash: b9e70716ad90a14bbed552d47f48d5a3317e5a62
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225705"
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>資料錄集：取得 SUM 和其他彙總結果 (ODBC)

> [!NOTE]
> Visual Studio 2019 和更新版本中未提供「MFC ODBC 消費者」精靈。 您仍然可以手動建立消費者。

本主題適用於 MFC ODBC 類別。

本主題說明如何使用下列 [SQL](../../data/odbc/sql.md) 關鍵字取得彙總結果：

- **SUM**：計算資料行中具有數值資料類型之值的總計。

- **MIN**：擷取資料行中具有數值資料類型的最小值。

- **MAX**：擷取資料行中具有數值資料類型的最大值。

- **AVG**：計算資料行中具有數值資料類型之所有值的平均值。

- **COUNT**：計算任何資料類型的資料行中的資料錄數目。

您可以使用這些 SQL 函式，取得資料來源中資料錄的統計相關資訊，而不是從資料來源擷取資料錄。 建立的資料錄集通常由包含一個值的單一資料錄 (如果所有資料行都是彙總值) 所組成  （如果您使用**GROUP by**子句，可能會有一個以上的記錄）。這個值是由 SQL 函數執行的計算或提取結果。

> [!TIP]
> 若要將 SQL **GROUP BY** 子句 (而且可能是 **HAVING** 子句) 加入到您的 SQL 陳述式中，請將其附加至 `m_strFilter` 的結尾。 例如：

```
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";
```

您可以透過篩選和排序資料行，限制您用來取得彙總結果之資料錄的數目。

> [!CAUTION]
> 某些彙總運算子會從它們彙總的資料行，傳回不同的資料類型。

- **SUM**和**AVG**可能會傳回下一個較大的資料類型（例如，呼叫 with 會傳回 **`int`** **LONG**或 **`double`** ）。

- 不論目標資料行是什麼類型，**COUNT** 通常會傳回 **LONG**。

- **MAX** 和 **MIN** 會傳回與所計算之資料行相同的資料類型。

     例如，「**加入類別**」 wizard **`long`** `m_lSales` 會建立以容納「銷售」資料行，但您必須將此取代為 `double m_dblSumSales` 資料成員，以容納匯總結果。 請參閱下列範例。

#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>若要取得資料錄集的彙總結果

1. 建立包含您要取得彙總結果所在資料行的資料錄集，如[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述。

1. 修改資料錄集的 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 函式。 將表示資料行名稱 ([RFX](../../data/odbc/record-field-exchange-using-rfx.md) 函式呼叫的第二個引數) 字串取代為表示資料行上彙總函式的字串。 例如，取代：

    ```
    RFX_Long(pFX, "Sales", m_lSales);
    ```

     成為：

    ```
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)
    ```

1. 開啟資料錄集。 彙總作業的結果會留在 `m_dblSumSales` 中。

> [!NOTE]
> 精靈實際上會指派沒有匈牙利文字首的資料成員名稱。 例如，精靈會為 Sales 資料行產生 `m_Sales`，而非稍早用於圖例的 `m_lSales` 名稱。

如果您要使用 [CRecordView](../../mfc/reference/crecordview-class.md) 類別檢視資料，必須變更 DDX 函式呼叫，才能顯示新的資料成員值；在此案例中，將其從下列內容變更為：

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);
```

變更為：

```
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);
```

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[記錄集：記錄集選取記錄的方式（ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
