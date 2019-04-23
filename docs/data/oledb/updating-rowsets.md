---
title: 更新資料列集
ms.date: 10/19/2018
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
ms.openlocfilehash: 7151d897469993b2f9be3575eb11a08844af3c69
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028356"
---
# <a name="updating-rowsets"></a>更新資料列集

基本資料庫作業是更新，或將資料寫入至資料存放區。 OLE DB 的更新機制很簡單：您的消費者應用程式會設定繫結資料成員值，接著將這些值寫入資料列集；消費者即可要求提供者更新該資料存放區。

取用者可以完成下列種類的資料列集資料的更新： 設定資料列中的資料行值、 插入資料列，並刪除資料列。 若要完成這些作業，OLE DB 範本類別[CRowset](../../data/oledb/crowset-class.md)實作[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))介面，並覆寫下列介面方法：

- [SetData](../../data/oledb/crowset-setdata.md)變更資料行值的資料列集資料列中，它相當於 SQL UPDATE 命令。

- [插入](../../data/oledb/crowset-insert.md)資料列插入資料列; 它相當於 SQL INSERT 命令。

- [刪除](../../data/oledb/crowset-delete.md)刪除資料列的資料列; 它相當於 SQL DELETE 命令。

## <a name="supporting-update-operations"></a>支援更新作業

當您建立與消費者**ATL OLE DB 消費者精靈**、 您可以支援更新作業，選取其中一項或多個三個核取方塊**變更**，**插入**，並**刪除**。 如果您選取這些選項，精靈將程式碼適當地修改以支援您選擇的變更類型。 不過，如果您未使用精靈，您需要下列的資料列集屬性設定為`VARIANT_TRUE`支援更新：

- `DBPROPVAL_UP_CHANGE` 可讓您變更資料列中的資料值。

- `DBPROPVAL_UP_INSERT` 可讓您插入資料列。

- `DBPROPVAL_UP_DELETE` 可讓您刪除資料列。

您可以依照下列所示來設定屬性：

```cpp
CDBPropSet ps(DBPROPSET_ROWSET);

ps.AddProperty(DBPROP_IRowsetChange, true);
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
```

如果一或多個資料行不是可寫入的變更、 插入或刪除作業可能會失敗。 修改您的資料指標對應以修正此問題。

## <a name="setting-data-in-rows"></a>設定資料列中的資料

[CRowset::SetData](../../data/oledb/crowset-setdata.md) 可以在目前資料列的一個或多個資料行中設定資料值。 下列程式碼設定繫結至資料行的資料成員的值`Name`並`Units in Stock`資料表的`Products`，然後呼叫`SetData`將這些值寫入第 100 的資料列的資料列集：

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

[CRowset::Insert](../../data/oledb/crowset-insert.md) 可以使用存取子資料，以建立和初始化一個新的資料列。 `Insert` 目前的資料列; 之後建立全新的資料列您必須指定是否要累加到下一個資料列的目前資料列或保持不動。 您可以設定 *bGetRow* 參數來達到這個目的：

```cpp
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)
```

- **false** (預設值) 指定目前資料列會累加到下一個資料列 (這樣一來，它會指向所插入的資料列)。

- **true**指定，目前資料列保持其所在。

下列程式碼設定的值繫結至資料表的資料行的資料成員`Products`，然後呼叫`Insert`資料列集的第 100 的資料列之後插入新的資料列，使用這些值。 我們建議您設定所有的資料行值，以避免在新的資料列中未定義的資料：

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

[CRowset::Delete](../../data/oledb/crowset-delete.md) 可以從資料列集刪除目前的資料列。 下列程式碼會呼叫`Delete`移除資料列集的第 100 的資料列：

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

除非您另外指定，會呼叫`SetData`， `Insert`，和`Delete`方法立即更新資料存放區。 但是您可以延後更新，以便消費者將所有的變更儲存在本機快取區，然後在您呼叫下列其中一種更新方法時，將它們傳送到資料存放區：

- [Crowset](../../data/oledb/crowset-update.md)傳輸任何暫止的變更目前的資料列自上次擷取或`Update`上呼叫。

- [Updateall](../../data/oledb/crowset-updateall.md)傳輸任何暫止的變更的所有資料列自上次擷取或`Update`上呼叫。

更新所使用的更新方法中，具有根據命令變更的特定意義和不會與 SQL 混淆**更新**命令 (`SetData`相當於 SQL**更新**命令).

延後的更新十分有用，例如，在一連串的銀行交易; 的情況如果一個交易被取消，您可以復原變更，因為最後一個認可之後，不要將傳送一系列之前的變更。 此外，提供者可以將這些變更全部放到一個網路呼叫中，這樣會更有效率。

若要支援延後的更新，您必須設定`DBPROP_IRowsetChange`屬性中所述的屬性以及**支援更新作業**:

```cpp
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);
```

當您呼叫`Update`或`UpdateAll`，方法會從本機快取的變更傳送到資料存放區，並接著再清除本機快取。 因為更新會傳送目前資料列的變更，很重要的應用程式會持續追蹤的資料列來更新，以及何時更新它。 下列程式碼示範如何更新兩個連續的資料列：

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

若要確定已經傳送暫止的變更，您應該呼叫`Update`再移至另一個資料列。 然而，如果這個動作很繁瑣或是沒有效率 (例如當應用程式需要更新數百個資料列) 時，您可以使用 `UpdateAll` 一次更新所有的資料列。

例如，如果第一個`Update`呼叫上述程式碼中遺漏，資料列 100 會維持不變，而資料列 101 會進行變更。 該動作之後，您的應用程式就必須呼叫`UpdateAll`或移回資料列 100 再呼叫`Update`更新該資料列。

最後，延後變更的主要原因是為了可以復原這些變更。 呼叫 [CRowset::Undo](../../data/oledb/crowset-undo.md) 可以將本機快取區變更的部分復原到任何暫止變更發生之前的資料存放區狀態。 請務必請注意，`Undo`不復原的本機快取的狀態一個步驟 （只在最新的變更之前的狀態）; 相反地，它會清除本機快取該資料列。 此外，`Undo`會影響在目前資料列。

## <a name="see-also"></a>另請參閱

[使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset 類別](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))<br/>
