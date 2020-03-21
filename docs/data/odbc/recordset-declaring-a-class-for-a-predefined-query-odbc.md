---
title: 資料錄集：宣告預先定義查詢的類別 (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: 6338de99bf9c3e19e6e15ffbe0bcf5caab066ed8
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079841"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>資料錄集：宣告預先定義查詢的類別 (ODBC)

> [!NOTE]
> Visual Studio 2019 及更新版本中未提供 MFC ODBC 消費者精靈。 您仍然可以手動建立消費者。

本主題適用於 MFC ODBC 類別。

本主題說明如何針對預先定義的查詢 (有時稱為預存程序，例如，在 Microsoft SQL Server 中)，建立資料錄集類別。

> [!NOTE]
>  本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果實作大量資料列擷取，程序會非常類似。 若要瞭解會執行大量資料列提取的記錄集之間的差異，以及不會執行的記錄集，請參閱[記錄集：提取大量資料（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

某些資料庫管理系統 (DBMS) 可讓您建立預先定義的查詢，並從您的應用程式呼叫它，例如函式。 查詢有名稱，可能會接受參數，而且可能會傳回資料錄。 本主題中的程序描述如何呼叫可傳回資料錄 (而且可能會接受參數) 的預先定義查詢。

資料庫類別不支援更新預先定義的查詢。 快照集預先定義的查詢與動態集預先定義的查詢之間的差異不在於是否能夠更新，而是在於對其他使用者 (或您程式中的其他資料錄集) 所做的變更是否會顯示在資料錄集中。

> [!TIP]
>  您不需要資料錄集，就可以呼叫不會傳回資料錄的預先定義查詢。 準備 SQL 陳述式，如下所述，但請藉由呼叫 `CDatabase` 成員函式 [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) 來執行它。

您可以建立單一資料錄集類別，以管理呼叫預先定義的查詢，但必須自己執行某些工作。 此精靈不支援特別針對這個用途建立一個類別。

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>若要建立類別來呼叫預先定義的查詢 (預存程序)

1. 使用 [MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md) 從 [加入類別] 為提供查詢所傳回的最多資料行的資料表建立資料錄集類別。 這為您提供了一個良好的開端。

1. 針對查詢會傳回但精靈未為您建立的之任何資料表的任何資料行，手動新增欄位資料成員。

   例如，如果查詢所傳回的三個資料行中，每個都來自兩個額外的資料表，請將 (適當資料類型的) 六個欄位資料成員新增至類別。

1. 在類別的 [DoFieldExchange](../../data/odbc/record-field-exchange-rfx.md) 成員函式中，手動新增 [RFX](../../mfc/reference/crecordset-class.md#dofieldexchange) 函式呼叫，其中一個會對應到每個新增的欄位資料成員的資料類型。

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  您必須知道在結果集中傳回之資料行的資料類型和順序。 RFX 函式在 `DoFieldExchange` 中呼叫的順序必須符合結果集資料行的順序。

1. 在資料錄集類別建構函式中，為新的欄位資料成員手動新增初始化。

   此外，您也必須為 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 資料成員遞增初始化值。 此精靈會寫入初始化，但只會涵蓋它為您新增的欄位資料成員。 例如：

    ```cpp
    m_nFields += 6;
    ```

   部分資料類型不應該在這裡初始化，例如，`CLongBinary` 或位元組陣列。

1. 如果查詢接受參數，請為每個參數新增一個參數資料成員、為每個參數新增一個 RFX 函式呼叫，並為每個參數新增一個初始化。

1. 您必須針對每個已新增的參數遞增 `m_nParams`，如同您為此程序的步驟 4 中新增的欄位遞增 `m_nFields` 一樣。 如需詳細資訊，請參閱[記錄集：參數化記錄集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

1. 使用下列格式，手動撰寫 SQL 陳述式字串：

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   其中 **CALL** 是一個 ODBC 關鍵字、**proc-name** 是資料來源上已知查詢的名稱，而 "?" 項目是您在執行階段提供給資料錄集之參數值的預留位置 (如果有的話)。 下列範例會為一個參數準備一個預留位置：

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. 在開啟資料錄集的程式碼中，設定資料錄集之參數資料成員的值，然後呼叫 `Open` 成員函式，進而傳遞您的 SQL 字串，供 *lpszSQL* 參數使用。 或者，取代類別中由 `GetDefaultSQL` 成員函式所傳回的字串。

下列範例示範呼叫名為 `Delinquent_Accts` 之預先定義查詢的程序，其中一個銷售地區號碼會採用一個參數。 此查詢會傳回三個資料行：`Acct_No`、`L_Name`、`Phone`。 所有資料行都來自 [客戶] 資料表。

下列資料錄集會針對查詢所傳回的資料行，以及銷售地區號碼在執行階段要求的參數，指定欄位資料成員。

```cpp
class CDelinquents : public CRecordset
{
// Field/Param Data
    LONG m_lAcct_No;
    CString m_strL_Name;
    CString m_strPhone;
    LONG m_lDistParam;
    // ...
};
```

此類別宣告如同精靈所寫入的類別宣告，但成員手動新增的 `m_lDistParam` 除外。 這裡不會顯示其他成員。

下一個範例示範 `CDelinquents` 建構函式中資料成員的初始化。

```cpp
CDelinquents::CDelinquents(CDatabase* pdb)
   : CRecordset(pdb)
{
    // Wizard-generated params:
    m_lAcct_No = 0;
    m_strL_Name = "";
    m_strPhone = "";
    m_nFields = 3;
    // User-defined params:
    m_nParams = 1;
    m_lDistParam = 0;
}
```

請注意 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 和 [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) 的初始化。 精靈會初始化 `m_nFields`，而您初始化 `m_nParams`。

下一個範例示範 `CDelinquents::DoFieldExchange` 中的 RFX 函式：

```cpp
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Long(pFX, "Acct_No", m_lAcct_No);
    RFX_Text(pFX, "L_Name", m_strL_Name);
    RFX_Text(pFX, "Phone", m_strPhone);
    pFX->SetFieldType(CFieldExchange::param);
    RFX_Long(pFX, "Dist_No", m_lDistParam);
}
```

除了為三個傳回的資料行進行 RFX 呼叫之外，此程式碼還會管理您在執行階段所傳遞之參數的繫結。 此參數會鍵入到 `Dist_No` (地區號碼) 資料行。

下一個範例示範如何設定 SQL 字串，以及如何使用它來開啟資料錄集。

```cpp
// Construct a CDelinquents recordset object
CDelinquents rsDel( NULL );
CString strSQL = "{CALL Delinquent_Accts (?)}"
// Specify a parameter value (obtained earlier from the user)
rsDel.m_lDistParam = lDistrict;
// Open the recordset and run the query
if( rsDel.Open( CRecordset::snapshot, strSQL ) )
    // Use the recordset ...
```

此程式碼會建構一個快照集、為其傳遞一個稍早取自使用者的參數，然後呼叫預先定義的查詢。 當查詢執行時，它會針對指定的銷售地區傳回資料錄。 每一筆資料錄都包含帳戶號碼、客戶姓氏和客戶電話號碼的資料行。

> [!TIP]
>  您可以從預存程序處理傳回值 (輸出參數)。 如需詳細資訊和範例，請參閱 [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：重新查詢資料錄集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[資料錄集：宣告資料表的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[資料錄集：執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)