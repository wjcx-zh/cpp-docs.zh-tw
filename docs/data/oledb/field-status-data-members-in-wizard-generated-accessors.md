---
title: 在精靈產生的存取子中的欄位狀態資料成員
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: a6623cb02f14650d92e4adabed749b0b37725d45
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707552"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>在精靈產生的存取子中的欄位狀態資料成員

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 消費者精靈。 您仍然可以手動加入功能。 如需詳細資訊，請參閱[未使用精靈建立消費者](creating-a-consumer-without-using-a-wizard.md)。

::: moniker-end

::: moniker range="<=vs-2017"

當您使用 **ATL OLE DB 消費者精靈**來建立消費者時，精靈會針對您在資料行對應中指定的每個欄位，於使用者記錄類別中產生資料成員。 每個資料成員的型別均為 `DWORD`，並包含對應至其個別欄位的狀態值。

例如，針對資料成員 *m_OwnerID*，精靈會為欄位狀態產生一個額外的資料成員 (*dwOwnerIDStatus*)，並為欄位長度產生另一個成員 (*dwOwnerIDLength*)。 它也會產生含 COLUMN_ENTRY_LENGTH_STATUS 項目的資料行對應。

這會以下列程式碼顯示：

```cpp
class CAuthorsAccessor
{
public:
   LONG m_AuID;
   TCHAR m_Author[53];
   LONG m_YearBorn;

   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;

   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;

    DEFINE_COMMAND_EX(CAuthorsAccessor, L" \
    SELECT \
        AuID, \
        Author, \
        YearBorn \
        FROM dbo.Authors")

    BEGIN_COLUMN_MAP(CAuthorsAccessor)
       COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)
       COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)
    END_COLUMN_MAP()
...
```

> [!NOTE]
> 如果您修改使用者記錄類別或撰寫自己的消費者，資料變數必須出現在狀態和長度變數之前。

您可以基於偵錯目的來使用狀態值。 如果 **ATL OLE DB 消費者精靈**所產生的程式碼會產生編譯錯誤 (例如 DB_S_ERRORSOCCURRED 或 DB_E_ERRORSOCCURRED)，您應該先查看欄位狀態資料成員的目前值。 那些具有非零值的成員會對應至衝突的資料行。

您也可以使用狀態值來設定特定欄位的 NULL 值。 如果您想要將欄位值區分為 NULL 而非零，這樣做可為您提供協助。 您必須自行決定 NULL 是否為有效值或特殊值，並決定應用程式應該如何處理它。 OLE DB 會定義 DBSTATUS_S_ISNULL 作為指定泛型 NULL 值的正確方法。 如果消費者讀取資料且值為 Null，就會將狀態欄位設定為 DBSTATUS_S_ISNULL。 如果消費者想要設定 NULL 值，則消費者會先將狀態值設定為 DBSTATUS_S_ISNULL，然後再呼叫提供者。

接下來，開啟 Oledb.h 並搜尋 DBSTATUSENUM。 您接著可以針對 DBSTATUSENUM 列舉值來比對非零狀態的數值。 如果列舉名稱不足以告訴您哪裡有錯誤，請參閱 [OLE DB 程式設計人員指南](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)中**繫結資料值**一節的**狀態**主題。 本主題包含在取得或設定資料時所使用的狀態值表格。 如需長度值的相關資訊，請參閱同一節中的**長度**主題。

## <a name="retrieving-the-length-or-status-of-a-column"></a>擷取資料行的長度或狀態

您可以擷取可變長度資料行的長度或資料行的狀態 (例如，檢查 DBSTATUS_S_ISNULL)：

- 若要取得長度，使用 COLUMN_ENTRY_LENGTH 巨集。

- 若要取得狀態，使用 COLUMN_ENTRY_STATUS 巨集。

- 若要取得這兩者，使用 COLUMN_ENTRY_LENGTH_STATUS，如同所示：

    ```cpp
    class CProducts
    {
    public:
       char      szName[40];
       long      nNameLength;
       DBSTATUS   nNameStatus;

    BEGIN_COLUMN_MAP(CProducts)
    // Bind the column to CProducts.m_ProductName.
    // nOrdinal is zero-based, so the column number of m_ProductName is 1.
       COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)
    END_COLUMN_MAP()
    };
    ```

- 然後，存取長度和/或狀態，如同所示：

    ```cpp
    CTable<CAccessor<CProducts >> product;
    CSession session;

    product.Open(session, "Product");

    while (product.MoveNext() == S_OK)
    {
       // Check the product name isn't NULL before tracing it
       if (product.nNameStatus == DBSTATUS_S_OK)
          ATLTRACE("%s is %d characters\n", product.szName, product.nNameLength);
    }
    ```

當您使用 `CDynamicAccessor` 時，即會自動繫結長度和狀態。 若要擷取長度和狀態值，使用 `GetLength` 和 `GetStatus` 成員函式。

::: moniker-end

## <a name="see-also"></a>另請參閱

[使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)