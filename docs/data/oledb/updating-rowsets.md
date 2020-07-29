---
title: 更新資料列集
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
ms.openlocfilehash: 22e362170d645574b40070c6db39c2576d3ae9c8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212939"
---
# <a name="updating-rowsets"></a>更新資料列集

更新 (或將資料寫入至) 資料存放區是一個基本的資料庫作業。 OLE DB 的更新機制很簡單：您的消費者應用程式會設定繫結資料成員值，接著將這些值寫入資料列集；消費者即可要求提供者更新該資料存放區。

消費者可以在資料列集資料上完成下列各種更新：在資料列內設定資料行值、插入資料列，以及刪除資料列。 為了完成這些作業，OLE DB 範本類別 [CRowset](../../data/oledb/crowset-class.md) 會實作 [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) 介面，並覆寫下列介面方法：

- [SetData](../../data/oledb/crowset-setdata.md) 會在資料列集的資料列中變更資料行值；它相當於 SQL UPDATE 命令。

- [Insert](../../data/oledb/crowset-insert.md) 會將資料列插入至資料列集；它相當於 SQL INSERT 命令。

- [Delete](../../data/oledb/crowset-delete.md) 會刪除資料列集的資料列；它相當於 SQL DELETE 命令。

## <a name="supporting-update-operations"></a>支援更新作業

> [!NOTE]
> Visual Studio 2019 及更新版本中未提供 ATL OLE DB 消費者精靈。 您仍能手動新增功能。 如需詳細資訊，請參閱[未使用精靈建立消費者](creating-a-consumer-without-using-a-wizard.md)。

當您使用**ATL OLE DB 取用者 Wizard**建立取用者時，您可以藉由選取三個核取方塊 [**變更**]、[**插入**] 和 [**刪除**] 中的一或多個，以支援更新作業。 如果您選取這些選項，精靈會適當地修改程式碼以支援您選擇的變更類型。 不過，如果您未使用精靈，則需將下列資料列集屬性設定為 `VARIANT_TRUE` 以支援更新：

- `DBPROPVAL_UP_CHANGE` 可讓您變更資料列中的資料值。

- `DBPROPVAL_UP_INSERT` 可讓您插入資料列。

- `DBPROPVAL_UP_DELETE` 可讓您刪除資料列。

您可以依照下列所示來設定屬性：

```cpp
CDBPropSet ps(DBPROPSET_ROWSET);

ps.AddProperty(DBPROP_IRowsetChange, true);
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
```

如果有一或多個資料行無法寫入，則變更、插入或刪除作業可能會失敗。 請修改您的資料指標對應以修正這個問題。

## <a name="setting-data-in-rows"></a>設定資料列中的資料

[CRowset::SetData](../../data/oledb/crowset-setdata.md) 可以在目前資料列的一個或多個資料行中設定資料值。 下列程式碼會設定繫結至 `Products` 資料表之 `Name` 和 `Units in Stock` 資料行的資料成員值，接著呼叫 `SetData`，以將那些值寫入至資料列集的第 100 個資料列：

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_UnitsInStock = 10000;

// Set the data
HRESULT hr = product.SetData();
```

## <a name="inserting-rows-into-rowsets"></a>將資料列插入至資料列集

[CRowset::Insert](../../data/oledb/crowset-insert.md) 可以使用存取子資料，以建立和初始化一個新的資料列。 `Insert` 會在目前資料列之後建立一個全新的資料列；您必須指定是否要將目前資料列累加到下一個資料列，或使其保持不變。 您可以設定 *bGetRow* 參數來達到這個目的：

```cpp
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)
```

- **`false`**（預設值）指定目前的資料列遞增到下一個資料列（在此情況下，它會指向插入的資料列）。

- **`true`** 指定目前的資料列保持在其所在的位置。

下列程式碼會設定繫結至 `Products` 資料表資料行的資料成員值，接著呼叫 `Insert`，以將含那些值的新資料列插入至資料列集的第 100 個資料列之後。 建議您設定所有資料行值，以避免新資料列中出現未定義的資料：

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Set the column values for a row of the Product table, then insert the row
product.m_ProductID = 101;
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_SupplierID = 27857;
product.m_CategoryID = 372;
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit, _T( "Pack of 10" ) );

product.m_UnitPrice = 20;
product.m_UnitsInStock = 10000;
product.m_UnitsOnOrder = 5201;
product.m_ReorderLevel = 5000;
product.m_Discontinued = false;

// You must also initialize the status and length fields before setting/inserting data
// Set the column status values
m_dwProductIDStatus = DBSTATUS_S_OK;
m_dwProductNameStatus = DBSTATUS_S_OK;
m_dwSupplierIDStatus = DBSTATUS_S_OK;
m_dwCategoryIDStatus = DBSTATUS_S_OK;
m_dwQuantityPerUnitStatus = DBSTATUS_S_OK;
m_dwUnitPriceStatus = DBSTATUS_S_OK;
m_dwUnitsInStockStatus = DBSTATUS_S_OK;
m_dwUnitsOnOrderStatus = DBSTATUS_S_OK;
m_dwReorderLevelStatus = DBSTATUS_S_OK;
m_dwDiscontinuedStatus = DBSTATUS_S_OK;

// Set the column length value for column data members that are not fixed-length types.
// The value should be the length of the string that you are setting.
m_dwProductNameLength = 6;             // "Candle" has 6 characters
m_dwQuantityPerUnitLength = 10;        // "Pack of 10" has 10 characters

// Insert the data
HRESULT hr = product.Insert();
```

如需更詳細的範例，請參閱 [CRowset::Insert](../../data/oledb/crowset-insert.md)。

如需設定狀態和長度資料成員的詳細資訊，請參閱 [在精靈產生的存取子中的欄位狀態資料成員](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。

## <a name="deleting-rows-from-rowsets"></a>從資料列集刪除資料列

[CRowset::Delete](../../data/oledb/crowset-delete.md) 可以從資料列集刪除目前的資料列。 下列程式碼會呼叫 `Delete` 來移除資料列集的第 100 個資料列：

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Delete the row
HRESULT hr = product.Delete();
```

## <a name="immediate-and-deferred-updates"></a>立即和延後更新

除非您指定其他方法，否則呼叫 `SetData`、`Insert` 和 `Delete` 方法會立即更新資料存放區。 但是您可以延後更新，以便消費者將所有的變更儲存在本機快取區，然後在您呼叫下列其中一種更新方法時，將它們傳送到資料存放區：

- [CRowset::Update](../../data/oledb/crowset-update.md) 會傳送目前資料列自上次擷取或對其進行 `Update` 呼叫之後所做的任何暫止變更。

- [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) 會傳送所有資料列自上次擷取或對其進行 `Update` 呼叫之後所做的任何暫止變更。

更新 (如更新方法所使用) 含有對命令進行變更的特定意義，請勿將其和 SQL **UPDATE** 命令混淆 (`SetData` 相當於 SQL **UPDATE** 命令)。

延遲更新在某些情況下很有用，例如，一連串的銀行交易；如果取消了其中一個交易，則您可以復原該變更，因為您要在認可最後一個交易完成後，才會傳送這一連串的變更。 此外，提供者可以將這些變更全部放到一個網路呼叫中，這樣會更有效率。

若要支援延遲更新，您必須設定 `DBPROP_IRowsetChange` 屬性以及**支援更新作業**中所述的屬性：

```cpp
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);
```

當您呼叫 `Update` 或 `UpdateAll` 時，方法會將變更從本機快取傳送到資料存放區，接著清除本機快取。 因為更新只會傳送目前資料列的變更，所以，讓應用程式持續追蹤要更新的資料列及何時更新非常重要。 下列程式碼示範如何更新兩個連續的資料列：

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Wick" ) );

product.m_UnitsInStock = 10000;

HRESULT hr = product.SetData();  // No changes made to row 100 yet
product.Update();                 // Update row 100 now

// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table
product.MoveNext();

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName _T( "Wax" ) );

product.m_UnitsInStock = 500;

HRESULT hr = product.SetData();  // No changes made to row 101 yet
product.Update();                 // Update row 101 now
```

為了確保會傳送暫止的變更，您應該先呼叫 `Update`，然後再移至其他資料列。 然而，如果這個動作很繁瑣或是沒有效率 (例如當應用程式需要更新數百個資料列) 時，您可以使用 `UpdateAll` 一次更新所有的資料列。

例如，如果上述程式碼遺漏了第一個 `Update` 呼叫，則資料列 100 會保持不變，而資料列 101 會遭到變更。 在那之後，應用程式可能必須呼叫 `UpdateAll`，或移回資料列 100 並針對要更新的資料列呼叫 `Update`。

最後，延後變更的主要原因是為了可以復原這些變更。 呼叫 [CRowset::Undo](../../data/oledb/crowset-undo.md) 可以將本機快取區變更的部分復原到任何暫止變更發生之前的資料存放區狀態。 請務必注意，`Undo` 不會使本機快取的狀態復原一個步驟 (即最近一次變更的前一個狀態)；相反地，它會清除該資料列的本機快取。 此外，`Undo` 只會影響目前的資料列。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 取用者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset 類別](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))<br/>
