---
title: 消費者精靈產生的方法 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c0e03d24f61b3eba1ff4c6fa1e4d888a0252a21b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="consumer-wizard-generated-methods"></a>消費者精靈產生的方法
ATL OLE DB 消費者精靈和 MFC 應用程式精靈產生的您應該注意的特定功能。 請注意，某些方法會實作以不同的方式在屬性化專案中，因此有一些警告。以下被涵蓋每個案例。 如需檢視插入程式碼的相關資訊，請參閱 [插入程式碼偵錯](/visualstudio/debugger/how-to-debug-injected-code)。  
  
-   `OpenAll` 開啟資料來源，資料列集，並在有提供書籤會開啟。  
  
-   `CloseAll` 關閉所有開啟的資料列集並釋放所有的命令執行。  
  
-   `OpenRowset` 會呼叫 OpenAll 開啟取用者的資料列集或資料列集。  
  
-   `GetRowsetProperties` 擷取資料列集的屬性集的屬性可以設定的指標。  
  
-   `OpenDataSource` 使用初始化字串中指定的資料來源就會開啟**資料連結屬性** 對話方塊。  
  
-   `CloseDataSource` 關閉資料來源中適當的方式。  
  
## <a name="openall-and-closeall"></a>OpenAll 和 CloseAll  
  
```  
HRESULT OpenAll();   

void CloseAll();  
```  
  
 下列範例會示範如何呼叫`OpenAll`和`CloseAll`當您重複執行相同的命令。 中的程式碼範例做比較[ccommand:: Close](../../data/oledb/ccommand-close.md)，其中顯示會呼叫一種變化**關閉**和`ReleaseCommand`而不是`CloseAll`。  
  
```  
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
  
## <a name="remarks"></a>備註  
 請注意，如果您定義`HasBookmark`方法，`OpenAll`程式碼會設定 DBPROP_IRowsetLocate 屬性; 請確定您只有這樣如果您的提供者支援該屬性。  
  
## <a name="openrowset"></a>OpenRowset  
  
```  
// OLE DB Template version:   
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);  
```  
  
 **OpenAll**呼叫此方法來開啟資料列集或資料列集取用者。 一般而言，您不需要呼叫`OpenRowset`除非您想要使用多個資料來源/工作階段/資料列集。 `OpenRowset` 在命令或資料表類別標頭檔宣告：  
  
```  
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
  
 屬性會以不同的方式實作這個方法。 這個版本會接受工作階段物件和預設值為 db_command 中, 指定的命令字串，雖然您可以傳遞不同的命令字串。 請注意，如果您定義`HasBookmark`方法，`OpenRowset`程式碼會設定 DBPROP_IRowsetLocate 屬性; 請確定您只有這樣如果您的提供者支援該屬性。  
  
```  
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
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet);  
```  
  
 這個方法會擷取資料列集的屬性集; 的指標若要設定屬性，例如 DBPROP_IRowsetChange，您可以使用這個指標。 `GetRowsetProperties` 用於使用者記錄類別，如下所示。 您可以修改這個程式碼以設定其他資料列集屬性：  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
## <a name="remarks"></a>備註  
 您不應定義為全域`GetRowsetProperties`方法因為它可能與其中一個衝突所定義的精靈。 請注意，這個精靈產生的方法，您會得到與建立樣板並屬性化專案;屬性不會插入這個程式碼。  
  
## <a name="opendatasource-and-closedatasource"></a>OpenDataSource 和 CloseDataSource  
  
```  
HRESULT OpenDataSource();   

void CloseDataSource();  
```  
  
## <a name="remarks"></a>備註  
 在精靈中定義的方法`OpenDataSource`和`CloseDataSource`;`OpenDataSource`呼叫[cdatasource:: Openfrominitializationstring](../../data/oledb/cdatasource-openfrominitializationstring.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用精靈建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)