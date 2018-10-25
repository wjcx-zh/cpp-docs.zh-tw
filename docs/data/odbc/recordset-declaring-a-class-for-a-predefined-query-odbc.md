---
title: 資料錄集： 宣告預先定義的查詢 (ODBC) 的類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 187b24b45ca24d45f6dd0f3f38cf62120633c790
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071241"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>資料錄集：宣告預先定義查詢的類別 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題說明如何建立預先定義的查詢 （有時稱為預存程序，與 Microsoft SQL Server） 的資料錄集類別。

> [!NOTE]
>  本主題適用於物件衍生自`CRecordset`的大量資料列中擷取尚未實作。 如果實作大量資料列擷取時，程序是非常類似。 若要了解實作與不實作大量資料列擷取的資料錄集之間的差異，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

某些資料庫管理系統 (Dbms) 可讓您建立預先定義的查詢，並從您的應用程式函式呼叫它。 查詢的名稱、 可能不接受參數，並可能會傳回記錄。 本主題中的程序描述如何呼叫預先定義的查詢傳回的記錄 （並可能接受參數）。

資料庫類別不支援更新預先定義的查詢。 快照集的預先定義的查詢與動態資料預先定義的查詢之間的差異不是可更新性，但其他使用者 （或您的程式中的其他資料錄集） 所做的變更是否顯示在資料錄集。

> [!TIP]
>  您不需要呼叫預先定義的查詢不會傳回記錄的資料錄集。 準備 SQL 陳述式，如下所述，但執行藉由呼叫`CDatabase`成員函式[ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)。

您可以建立單一資料錄集類別，以管理呼叫預先定義的查詢，但某些工作必須自己執行。 精靈不支援建立一個類別特別針對這個用途。

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>若要建立的類別呼叫預先定義的查詢 （預存程序）

1. 使用[MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)從**加入類別**建立資料表，以便共同完成最查詢所傳回的資料行的資料錄集類別。 這可讓您著手。

1. 手動新增的任何資料表的查詢會傳回，但精靈未為您建立的任何資料行的欄位資料成員。

   比方說，如果查詢會傳回三個資料行，從兩個額外的資料表，請將六個欄位資料成員 （適當的資料類型） 新增至類別。

1. 手動新增[RFX](../../data/odbc/record-field-exchange-rfx.md)函式呼叫[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)類別，各自對應到資料類型，每個成員函式加入的欄位資料成員。

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  您必須知道的資料類型和設定在結果中傳回的資料行的順序。 RFX 函式的順序呼叫`DoFieldExchange`必須符合的結果集資料行的順序。

1. 手動加入新的欄位資料成員的初始化資料錄集類別的建構函式中。

   此外，您也必須遞增的初始化值[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)資料成員。 精靈會將初始設定，但它只會涵蓋它會為您新增的欄位資料成員。 例如: 

    ```cpp
    m_nFields += 6;
    ```

   某些資料類型不應該初始化，比方說，`CLongBinary`或位元組陣列。

1. 如果查詢不接受參數，加入每個參數，分別 RFX 函式呼叫和初始化每個參數的資料成員。

1. 您必須遞增`m_nParams`針對每個已加入參數，如同`m_nFields`在此程序的步驟 4 中新增欄位。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

1. 手動撰寫下列形式的 SQL 陳述式字串：

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   其中**呼叫**是 ODBC 關鍵字，**處理序名稱**是查詢的名稱，因為它已知的資料來源，而 「？ 」 項目都是您提供給資料錄集在執行階段 （如果有的話） 的參數值的預留位置. 下列範例會準備一個參數的預留位置：

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. 在開啟資料錄集的程式碼，將設定資料錄集的參數的值資料成員，然後呼叫`Open`成員函式，傳遞您的 SQL 字串*lpszSQL*參數。 相反地，取代所傳回的字串或`GetDefaultSQL`類別中的成員函式。

下列範例示範的程序呼叫預先定義的查詢，名為`Delinquent_Accts`，這會採用一個參數的銷售地區的號碼。 此查詢會傳回三個資料行： `Acct_No`， `L_Name`， `Phone`。 所有的資料行是從 [客戶] 資料表。

下列的資料錄集指定此查詢會傳回和銷售的參數區域在執行階段要求的數字的資料行的欄位資料成員。

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

在精靈所編寫的是，除了為此類別宣告`m_lDistParam`手動加入的成員。 這裡不顯示其他成員。

下一個範例顯示中之資料成員初始化`CDelinquents`建構函式。

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

請注意，只針對[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)並[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)。 初始化精靈`m_nFields`; 您初始化`m_nParams`。

下一個範例顯示 RFX 函式中的`CDelinquents::DoFieldExchange`:

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

除了建立 RFX 呼叫三個傳回的資料行，此程式碼會管理您在執行階段所傳遞的參數繫結。 參數會做為索引鍵來`Dist_No`（學區號碼） 資料行。

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

此程式碼會建構一個快照集、 將其傳遞使用者，從稍早取得的參數和呼叫預先定義的查詢。 當查詢執行時，它會傳回指定的銷售地區的記錄。 每一筆記錄包含客戶編號、 客戶姓氏和客戶的電話號碼的資料行。

> [!TIP]
>  您可能想要處理從預存程序的傳回值 （輸出參數）。 如需詳細資訊和範例，請參閱 < [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：重新查詢資料錄集 (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[資料錄集：宣告資料表的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[資料錄集：執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)