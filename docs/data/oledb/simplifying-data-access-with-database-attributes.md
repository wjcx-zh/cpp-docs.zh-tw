---
title: 以資料庫屬性簡化資料存取
ms.date: 10/19/2018
helpviewer_keywords:
- attributes [C++], database
- attributes [C++], data access
- databases [C++], attributes
- data [C++], simplifying access
- data access [C++], database attributes
- database attributes [C++]
- OLE DB consumers [C++], database attributes
- attributes [C++], OLE DB consumer
ms.assetid: 560d2456-e307-4cb7-ba7b-4d0ed674697f
ms.openlocfilehash: 5fc30596058271523f64cc9108ee6f39eb5016fa
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444138"
---
# <a name="simplifying-data-access-with-database-attributes"></a>以資料庫屬性簡化資料存取

本主題示範如何使用資料庫屬性來簡化資料庫作業。

從資料庫存取訊號的基本方式，是針對資料庫中的特定資料表建立命令（或資料表）類別和使用者記錄類別。 資料庫屬性會簡化您先前必須執行的一些範本宣告。

為了示範資料庫屬性的使用，下列各節顯示兩個對等的資料表和使用者記錄類別宣告：第一個使用屬性，而第二個則使用 OLE DB 範本。 這類宣告程式碼通常會放在針對資料表或命令物件命名的標頭檔中，例如，作者 .h。

藉由比較這兩個檔案，您可以查看使用屬性有多簡單。 其中的差異包括：

- 使用屬性時，您只需要宣告一個類別： `CAuthors`，而使用範本時，您必須宣告兩個： `CAuthorsNoAttrAccessor` 和 `CAuthorsNoAttr`。

- 屬性化版本中的 `db_source` 呼叫相當於樣板宣告中的 `OpenDataSource()` 呼叫。

- 屬性化版本中的 `db_table` 呼叫相當於下列樣板宣告：

    ```cpp
    class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
    ```

- 屬性化版本中的 `db_column` 呼叫相當於樣板宣告中的資料行對應（請參閱 `BEGIN_COLUMN_MAP ... END_COLUMN_MAP`）。

屬性會為您插入使用者記錄類別宣告。 使用者記錄類別等於範本宣告中 `CAuthorsNoAttrAccessor`。 如果您的資料表類別是 `CAuthors`，插入的使用者記錄類別會命名為 `CAuthorsAccessor`，而且您只能在插入的程式碼中查看其宣告。 如需詳細資訊，請參閱[使用者記錄](../../data/oledb/user-records.md)中的「屬性插入的使用者記錄類別」。

在屬性化和樣板化程式碼中，您都必須使用 `CDBPropSet::AddProperty`來設定資料列集屬性。

如需本主題中所討論之屬性的詳細資訊，請參閱[OLE DB 取用者屬性](../../windows/ole-db-consumer-attributes.md)。

> [!NOTE]
> 需要下列 `include` 語句，才能編譯下列範例：

> ```cpp
> #include <atlbase.h>
> #include <atlplus.h>
> #include <atldbcli.h>
> ```

## <a name="table-and-accessor-declaration-using-attributes"></a>使用屬性的資料表和存取子宣告

下列程式碼會呼叫 table 類別上的 `db_source` 和 `db_table`。 `db_source` 指定要使用的資料來源和連接。 `db_table` 會插入適當的範本程式碼，以宣告資料表類別。 `db_column` 指定資料行對應，並插入存取子宣告。 您可以在任何支援 ATL 的專案中使用 OLE DB 取用者屬性。

以下是使用屬性的資料表和存取子宣告：

```cpp
//////////////////////////////////////////////////////////////////////
// Table and accessor declaration using attributes
// authors.h
//////////////////////////////////////////////////////////////////////

// Table class declaration
// (Note that you must provide your own connection string for db_source.)
[
   db_source(L"your connection string"),
   db_table("Authors")
]
class CAuthors
{
public:
   DBSTATUS m_dwAuIDStatus;
   DBSTATUS m_dwAuthorStatus;
   DBSTATUS m_dwYearBornStatus;
   DBLENGTH m_dwAuIDLength;
   DBLENGTH m_dwAuthorLength;
   DBLENGTH m_dwYearBornLength;
   [db_column("1", status = "m_dwAuIDStatus", length = "m_dwAuIDLength")] LONG m_AuID;
   [db_column("2", status = "m_dwAuthorStatus", length = "m_dwAuthorLength")] TCHAR m_Author[51];
   [db_column("3", status = "m_dwYearBornStatus", length = "m_dwYearBornLength")] SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
};
```

## <a name="table-and-accessor-declaration-using-templates"></a>使用範本的資料表和存取子宣告

以下是使用範本的資料表和存取子宣告。

```cpp
//////////////////////////////////////////////////////////////////////
// Table and user record class declaration using templates
// authors.h
//////////////////////////////////////////////////////////////////////

// User record class declaration
class CAuthorsNoAttrAccessor
{
public:
   DWORD m_dwAuIDStatus;
   DWORD m_dwAuthorStatus;
   DWORD m_dwYearBornStatus;
   DWORD m_dwAuIDLength;
   DWORD m_dwAuthorLength;
   DWORD m_dwYearBornLength;
   LONG m_AuID;
   TCHAR m_Author[51];
   SHORT m_YearBorn;
   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);
   }
   HRESULT OpenDataSource()
   {
      CDataSource _db;

HRESULT hr;
      hr = _db.OpenFromInitializationString(L"your connection string");
      if (FAILED(hr))
      {
#ifdef _DEBUG
         AtlTraceErrorRecords(hr);
#endif
         return hr;
      }
      return m_session.Open(_db);
   }
   void CloseDataSource()
   {
      m_session.Close();
   }
   operator const CSession&()
   {
      return m_session;
   }
   CSession m_session;
   BEGIN_COLUMN_MAP(CAuthorsNoAttrAccessor)
      COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, m_dwAuIDLength, m_dwAuIDStatus)
      COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, m_dwAuthorLength, m_dwAuthorStatus)
      COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, m_dwYearBornLength, m_dwYearBornStatus)
   END_COLUMN_MAP()
};
class CAuthorsNoAttr : public CTable<CAccessor<CAuthorsNoAttrAccessor>>
{
public:
   HRESULT OpenAll()
   {
HRESULT hr;
      hr = OpenDataSource();
      if (FAILED(hr))
         return hr;
      __if_exists(GetRowsetProperties)
      {
         CDBPropSet propset(DBPROPSET_ROWSET);
         __if_exists(HasBookmark)
         {
            propset.AddProperty(DBPROP_IRowsetLocate, true);
         }
         GetRowsetProperties(&propset);
         return OpenRowset(&propset);
      }
      __if_not_exists(GetRowsetProperties)
      {
         __if_exists(HasBookmark)
         {
            CDBPropSet propset(DBPROPSET_ROWSET);
            propset.AddProperty(DBPROP_IRowsetLocate, true);
            return OpenRowset(&propset);
         }
      }
      return OpenRowset();
   }
   HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
   {
HRESULT hr = Open(m_session, "Authors", pPropSet);
#ifdef _DEBUG
      if(FAILED(hr))
         AtlTraceErrorRecords(hr);
#endif
      return hr;
   }
   void CloseAll()
   {
      Close();
      CloseDataSource();
   }
};
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者屬性](../../windows/ole-db-consumer-attributes.md)
