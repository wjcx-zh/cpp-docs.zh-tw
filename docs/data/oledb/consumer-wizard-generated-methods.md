---
title: 消費者精靈產生的方法
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, wizard-generated classes and methods
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: ce2442909fd318187a1508300a75ff4f634b3410
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211506"
---
# <a name="consumer-wizard-generated-methods"></a>消費者精靈產生的方法

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 消費者精靈。 您仍然可以手動加入功能。

::: moniker-end

::: moniker range="<=vs-2017"

**ATL OLE DB 消費者精靈**和 **MFC 應用程式精靈**會產生一些您應該會注意到的函式。 部分方法在屬性化專案中是以不同的方式實作的，因此會有一些需要注意的事項；以下涵蓋每個案例。 如需檢視插入程式碼的相關資訊，請參閱 [插入程式碼偵錯](/visualstudio/debugger/how-to-debug-injected-code)。

- `OpenAll` 會開啟資料來源、資料列集以及書籤 (如果可用的話)。

- `CloseAll` 會關閉所有開啟的資料列集，並釋出所有的命令執行。

- `OpenRowset` 會呼叫 `OpenAll` 來開啟消費者的一或多個資料列集。

- `GetRowsetProperties` 會擷取設定屬性可以使用之資料列集屬性集的指標。

- `OpenDataSource` 會使用您在 [資料連結屬性] 對話方塊中指定的初始化字串，開啟資料來源。

- `CloseDataSource` 會以適當的方式關閉資料來源。

## <a name="openall-and-closeall"></a>OpenAll 和 CloseAll

```cpp
HRESULT OpenAll();

void CloseAll();
```

下列範例示範如何在您重複執行相同的命令時，呼叫 `OpenAll` 和 `CloseAll`。 比較 [CCommand::Close](../../data/oledb/ccommand-close.md) 中的程式碼範例，這會顯示呼叫 `Close` 和 `ReleaseCommand` 而不是 `CloseAll` 的變化。

```cpp
int main(int argc, char* argv[])
{
   HRESULT hr;

   hr = CoInitialize(NULL);

   CCustOrdersDetail rs;      // Your CCommand-derived class
   rs.m_OrderID = 10248;      // Open order 10248
   hr = rs.OpenAll();         // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the first command execution
   rs.Close();

   rs.m_OrderID = 10249;      // Open order 10249 (a new order)
   hr = rs.Open();            // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the second command execution;
   // Instead of rs.CloseAll() you could call
   // rs.Close() and rs.ReleaseCommand():
   rs.CloseAll();

   CoUninitialize();
   return 0;
}
```

### <a name="remarks"></a>備註

如果您定義 `HasBookmark` 方法，`OpenAll` 程式碼會設定 `DBPROP_IRowsetLocate` 屬性；請確定您只有在提供者支援該屬性時，才執行此操作。

## <a name="openrowset"></a>[OpenRowset]

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` 會呼叫這個方法來以開啟消費者中的一或多個資料列集。 一般而言，除非您想要使用多個資料來源/工作階段/資料列集，否則您不需要呼叫 `OpenRowset`。 `OpenRowset` 是在命令或資料表類別標頭檔中宣告的：

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
{
   HRESULT hr = Open(m_session, NULL, pPropSet);
   #ifdef _DEBUG
   if(FAILED(hr))
      AtlTraceErrorRecords(hr);
   #endif
   return hr;
}
```

屬性會以不同的方式實作這個方法。 此版本會採用預設為在 db_command 中指定之命令字串的工作階段物件和命令字串，但是您可以傳遞另一個不同的命令字串。 如果您定義 `HasBookmark` 方法，`OpenRowset` 程式碼會設定 `DBPROP_IRowsetLocate` 屬性；請確定您只有在提供者支援該屬性時，才執行此操作。

```cpp
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)
{

   DBPROPSET *pPropSet = NULL;
   CDBPropSet propset(DBPROPSET_ROWSET);
   __if_exists(HasBookmark)

   {
      propset.AddProperty(DBPROP_IRowsetLocate, true);
      pPropSet= &propset;
      }
...
}
```

## <a name="getrowsetproperties"></a>GetRowsetProperties

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet);
```

此方法會擷取資料列集屬性集的指標；您可以使用這個指標來設定屬性，例如 `DBPROP_IRowsetChange`。 `GetRowsetProperties` 用於使用者記錄類別，如下所示。 您可以修改此程式碼來設定其他資料列集屬性：

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="remarks"></a>備註

您不應該定義全域 `GetRowsetProperties` 方法，因為它可能會與精靈所定義的一個方法衝突。 這是精靈產生的方法，您可以使用範本和屬性化專案取得該方法；這些屬性不會插入此程式碼。

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource 和 CloseDataSource

```cpp
HRESULT OpenDataSource();

void CloseDataSource();
```

### <a name="remarks"></a>備註

此精靈會定義方法 `OpenDataSource` 和 `CloseDataSource`；`OpenDataSource` 會呼叫 [CDataSource::OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[使用精靈建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
