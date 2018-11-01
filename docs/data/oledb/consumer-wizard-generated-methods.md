---
title: 消費者精靈產生的方法
ms.date: 11/04/2016
helpviewer_keywords:
- OpenAll method
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- methods [C++], OLE DB Consumer Wizard-generated
- CloseDataSource method
- consumer wizard-generated classes and methods
- OpenDataSource method
- CloseAll method
- OpenRowset method
- GetRowsetProperties method
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: 4c364d0caccfc422b91a68e15704628a949ef67b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635795"
---
# <a name="consumer-wizard-generated-methods"></a>消費者精靈產生的方法

**ATL OLE DB 消費者精靈**並**MFC 應用程式精靈**產生您應該要注意的特定函式。 某些方法的實作方式不同在屬性化專案中，因此會有一些需要注意的事項;底下有涵蓋每個案例。 如需檢視插入程式碼的相關資訊，請參閱 [插入程式碼偵錯](/visualstudio/debugger/how-to-debug-injected-code)。

- `OpenAll` 會開啟資料來源，資料列集，並開啟書籤，如果它們可用。

- `CloseAll` 關閉所有開啟的資料列集並釋放所有的命令執行。

- `OpenRowset` 會呼叫`OpenAll`開啟取用者的資料列集或資料列集。

- `GetRowsetProperties` 擷取資料列集的屬性集的屬性可以設定的指標。

- `OpenDataSource` 開啟使用初始化字串中指定的資料來源**資料連結屬性** 對話方塊。

- `CloseDataSource` 關閉資料來源，以適當方式。

## <a name="openall-and-closeall"></a>OpenAll and CloseAll

```cpp
HRESULT OpenAll(); 

void CloseAll();
```

下列範例示範如何呼叫`OpenAll`和`CloseAll`當您重複執行相同的命令。 比較中的程式碼範例[ccommand:: Close](../../data/oledb/ccommand-close.md)，這會顯示呼叫變化`Close`並`ReleaseCommand`而不是`CloseAll`。

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

如果您定義`HasBookmark`方法中，`OpenAll`程式碼設定`DBPROP_IRowsetLocate`屬性; 請確定您只有這樣如果您的提供者支援該屬性。

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version: 
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` 呼叫這個方法，以開啟 取用者中的 資料列集或資料列集。 一般而言，您不需要呼叫`OpenRowset`除非您想要使用多個資料來源/工作階段/資料列集。 `OpenRowset` 命令或資料表類別標頭檔中宣告：

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

屬性會以不同的方式實作這個方法。 這個版本會將工作階段物件和預設 db_command，在指定的命令字串，雖然您可以傳遞一個不同的命令字串。 如果您定義`HasBookmark`方法中，`OpenRowset`程式碼設定`DBPROP_IRowsetLocate`屬性; 請確定您只有這樣如果您的提供者支援該屬性。

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

這個方法會擷取資料列集的屬性集; 的指標您可以使用這個指標來設定屬性，例如`DBPROP_IRowsetChange`。 `GetRowsetProperties` 可在使用者記錄類別，如下所示。 您可以修改此程式碼來設定額外的資料列集屬性：

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

您不應定義全域`GetRowsetProperties`方法因為它可能會與其中一個衝突所定義的精靈。 這是精靈產生的方法取得建立樣板並屬性化專案的專案。屬性不會插入此程式碼。

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource 和 CloseDataSource

```cpp
HRESULT OpenDataSource(); 

void CloseDataSource();
```

### <a name="remarks"></a>備註

精靈定義的方法`OpenDataSource`和`CloseDataSource`;`OpenDataSource`呼叫[cdatasource:: Openfrominitializationstring](../../data/oledb/cdatasource-openfrominitializationstring.md)。

## <a name="see-also"></a>另請參閱

[使用精靈建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)