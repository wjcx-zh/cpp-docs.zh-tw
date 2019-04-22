---
title: 在精靈產生的存取子中的欄位狀態資料成員
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
ms.openlocfilehash: dd650b7cafef78e23c23ddfef791c88b6b93727f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025068"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>在精靈產生的存取子中的欄位狀態資料成員

當您使用**ATL OLE DB 消費者精靈**建立消費者，精靈會產生資料成員在您指定資料行對應中的每個欄位的使用者記錄類別。 每個資料成員的類型是`DWORD`並包含對應至其個別欄位的狀態值。

例如，對於資料成員*m_OwnerID*，精靈會產生額外的資料成員的欄位狀態 (*dwOwnerIDStatus*)，另一個則欄位長度 (*dwOwnerIDLength*). 它也會產生資料行對應與 COLUMN_ENTRY_LENGTH_STATUS 項。

這是由下列程式碼所示：

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

您可以使用 [狀態] 值，以進行偵錯。 如果產生的程式碼**ATL OLE DB 消費者精靈**產生編譯錯誤，例如 DB_S_ERRORSOCCURRED 或 DB_E_ERRORSOCCURRED，您應該先查看欄位狀態資料成員的目前值。 具有非零的值會對應至衝突的資料行。

您也可以使用 [狀態] 值來設定特定欄位的 NULL 值。 這樣可協助您的情況下您想用來區別欄位值為 NULL，而不是零。 它是您必須決定 NULL 是否為有效的值或特殊值，並決定您的應用程式應該如何處理它。 OLE DB 定義為 DBSTATUS_S_ISNULL 指定泛用的 NULL 值的正確方法。 如果取用者讀取資料，此值為 null，會將 [狀態] 欄位設為 DBSTATUS_S_ISNULL。 如果取用者想要設定為 NULL 值，取用者狀態值設定為 DBSTATUS_S_ISNULL 之前呼叫提供者。

接下來，開啟 Oledb.h 並搜尋 DBSTATUSENUM。 然後，您可以比對的非零值的狀態，針對 DBSTATUSENUM 列舉值的數值。 如果列舉名稱不足以告訴您哪裡有錯誤，請參閱 <<c0>  **狀態**中的主題**繫結資料值**一節[OLE DB 程式設計人員指南](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)。 本主題包含的狀態時使用的值取得或設定資料的資料表。 長度值的詳細資訊，請參閱**長度**相同區段中的主題。

## <a name="retrieving-the-length-or-status-of-a-column"></a>擷取的長度或資料行的狀態

您可以擷取可變長度資料行的長度或資料行 （例如檢查 DBSTATUS_S_ISNULL，） 的狀態：

- 若要取得長度，請使用 COLUMN_ENTRY_LENGTH 巨集。

- 若要取得狀態，請使用 COLUMN_ENTRY_STATUS 巨集。

- 若要取得這兩個，請使用 COLUMN_ENTRY_LENGTH_STATUS，，如所示：

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

- 然後，在示存取的長度和/或狀態：

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

當您使用`CDynamicAccessor`，長度和狀態會為您會自動繫結。 若要擷取的長度和狀態的值，請使用`GetLength`和`GetStatus`成員函式。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)