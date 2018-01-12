---
title: "更新資料列集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5d0d34b3dee1fb4983f60c7e437c14025b4e3022
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="updating-rowsets"></a>更新資料列集
更新或將資料寫入資料存放區是一種基本資料庫作業。 OLE DB 的更新機制很簡單：您的消費者應用程式會設定繫結資料成員值，接著將這些值寫入資料列集；消費者即可要求提供者更新該資料存放區。  
  
 消費者可以在資料列集資料上執行下列更新類型：設定資料列的資料行值、插入資料列和刪除資料列。 若要執行這些作業，OLE DB 範本類別 [CRowset](../../data/oledb/crowset-class.md) 會實作 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) 介面來執行這些動作，並覆寫下列介面方法：  
  
-   [SetData](../../data/oledb/crowset-setdata.md) 可以變更在資料列集中的資料列資料行值；它的作用相當於 SQL UPDATE 命令。  
  
-   [Insert](../../data/oledb/crowset-insert.md) 可以將資料列插入至資料列集；它的作用相當於 SQL INSERT 命令。  
  
-   [Delete](../../data/oledb/crowset-delete.md) 可以刪除資料列集的資料列；它的作用相當於 SQL DELETE 命令。  
  
## <a name="supporting-update-operations"></a>支援更新作業  
 您可以在使用 [ATL OLE DB 消費者精靈] 建立消費者時，選取三個核取方塊 [變更] 、[插入] 和 [刪除] 中的一個或多個方塊以支援更新作業。 如果您選取了上述核取方塊，精靈會適當地修改程式碼以支援您選擇的變更類型。 然而，如果不是使用精靈，您便需要將下列資料列集屬性設定為 `VARIANT_TRUE` 才能支援更新：  
  
-   **DBPROPVAL_UP_CHANGE** 可讓您變更資料列中的資料值。  
  
-   **DBPROPVAL_UP_INSERT** 可讓您插入資料列。  
  
-   **DBPROPVAL_UP_DELETE** 可讓您刪除資料列。  
  
 您可以依照下列所示來設定屬性：  
  
```  
CDBPropSet ps(DBPROPSET_ROWSET);  
ps.AddProperty(DBPROP_IRowsetChange, true)  
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
```  
  
 如果出現一個或多個資料行無法寫入的情形，變更、插入或刪除等作業便可能會失敗。 請修改您的資料指標對應以修正這個問題。  
  
## <a name="setting-data-in-rows"></a>設定資料列中的資料  
 [CRowset::SetData](../../data/oledb/crowset-setdata.md) 可以在目前資料列的一個或多個資料行中設定資料值。 下列程式碼會設定繫結至 [產品] 資料表的 [名稱] 和 [庫存單位數量] 資料行的資料成員值，接著再呼叫 `SetData` ，將這些值寫入資料列集的第 100 個資料列：  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor> > product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table  
_tcscpy_s( product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  
product.m_UnitsInStock = 10000;  
  
// Set the data  
HRESULT hr = product.SetData( );  
```  
  
## <a name="inserting-rows-into-rowsets"></a>將資料列插入至資料列集  
 [CRowset::Insert](../../data/oledb/crowset-insert.md) 可以使用存取子資料，以建立和初始化一個新的資料列。 **Insert** 會在目前資料列之後建立全新的資料列；您必須指定目前資料列是否要累加到下一個資料列，或保持不動。 您可以設定 *bGetRow* 參數來達到這個目的：  
  
```  
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)  
```  
  
-   **false** (預設值) 指定目前資料列會累加到下一個資料列 (這樣一來，它會指向所插入的資料列)。  
  
-   **true** 指定目前資料列維持不動。  
  
 下列程式碼會設定繫結至 [產品] 資料表資料行的資料成員值，接著再呼叫 **Insert** ，在資料列集的第 100 個資料列之後插入包含這些值的新資料列。 我們建議您設定所有的資料行值，以免新資料列中出現未定義的資料。  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor> > product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Set the column values for a row of the Product table, then insert the row  
product.m_ProductID = 101;  
_tcscpy_s( product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  
product.m_SupplierID = 27857;  
product.m_CategoryID = 372;  
_tcscpy_s( product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit,  
           _T( "Pack of 10" ) );  
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
HRESULT hr = product.Insert( );  
```  
  
 如需更詳細的範例，請參閱 [CRowset::Insert](../../data/oledb/crowset-insert.md)。  
  
 如需設定狀態和長度資料成員的詳細資訊，請參閱 [在精靈產生的存取子中的欄位狀態資料成員](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)。  
  
## <a name="deleting-rows-from-rowsets"></a>從資料列集刪除資料列  
 [CRowset::Delete](../../data/oledb/crowset-delete.md) 可以從資料列集刪除目前的資料列。 下列程式碼會呼叫 **Delete** 以移除資料列集的第 100 個資料列：  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor> > product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Delete the row  
HRESULT hr = product.Delete( );  
```  
  
## <a name="immediate-and-deferred-updates"></a>立即和延後更新  
 除非您指定其他方法，否則 `SetData`、 **Insert**和 **Delete** 方法的呼叫會立即更新資料存放區。 但是您可以延後更新，以便消費者將所有的變更儲存在本機快取區，然後在您呼叫下列其中一種更新方法時，將它們傳送到資料存放區：  
  
-   [CRowset::Update](../../data/oledb/crowset-update.md) 會傳送目前資料列自上次擷取或 **Update** 呼叫之後任何暫止的變更。  
  
-   [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) 會傳送所有資料列自上次擷取或 **Update** 呼叫之後任何暫止的變更。  
  
 請注意，更新方法所用的更新具有根據命令變更的特定意義，請勿將其和 SQL UPDATE 命令混淆 (`SetData` 相當於 SQL UPDATE 命令)。  
  
 延後更新在某些情況下很有用，舉一連串的銀行交易來說，因為您會在認可最後一個交易完成後才傳送所有變更，所以如果一個交易被取消，您仍可復原變更。 此外，提供者可以將這些變更全部放到一個網路呼叫中，這樣會更有效率。  
  
 若要支援延後更新，除了＜支援更新作業＞中所述的屬性外，您還必須設定 **DBPROP_IRowsetChange** 屬性：  
  
```  
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);  
```  
  
 這些方法會在您呼叫 **Update** 或 `UpdateAll`時將本機快取區的變更傳送到資料存放區，接著再清除本機快取區。 因為更新只會傳送目前資料列的變更，所以應用程式要追蹤更新的資料列以及何時更新是很重要的。 下列程式碼示範如何更新兩個連續的資料列：  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor> > product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table  
_tcscpy_s( product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Wick" ) );  
product.m_UnitsInStock = 10000;  
HRESULT hr = product.SetData( );  // No changes made to row 100 yet  
product.Update();                 // Update row 100 now  
  
// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table  
product.MoveNext( );  
_tcscpy_s( product.m_ProductName, product.m_sizeOfProductName  
           _T( "Wax" ) );  
product.m_UnitsInStock = 500;  
HRESULT hr = product.SetData( );  // No changes made to row 101 yet  
product.Update();                 // Update row 101 now  
```  
  
 若要確定已經傳送暫止變更，您應該在移到另一個資料列之前呼叫 **Update** 。 然而，如果這個動作很繁瑣或是沒有效率 (例如當應用程式需要更新數百個資料列) 時，您可以使用 `UpdateAll` 一次更新所有的資料列。  
  
 例如，如果上述程式碼遺失了第一個 **Update** 呼叫，那麼資料列 100 會維持不變，而資料列 101 會進行變更。 在該動作之後，應用程式可能為了要更新資料列而必須呼叫 `UpdateAll` ，或是向後移動至資料列 100 再呼叫 **Update** 。  
  
 最後，延後變更的主要原因是為了可以復原這些變更。 呼叫 [CRowset::Undo](../../data/oledb/crowset-undo.md) 可以將本機快取區變更的部分復原到任何暫止變更發生之前的資料存放區狀態。 請注意， **Undo** 不會將本機快取區的狀態復原到上一個步驟 (僅最近一次變更之前的狀態)；相反地，它會清除該資料列的本機快取區。 此外， **Undo** 只會影響目前的資料列。  
  
## <a name="see-also"></a>請參閱  
 [使用 OLE DB 消費者樣板](../../data/oledb/working-with-ole-db-consumer-templates.md)   
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)