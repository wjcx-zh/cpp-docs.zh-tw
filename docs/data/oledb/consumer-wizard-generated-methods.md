---
title: "消費者精靈產生的方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "插入屬性的類別和方法"
  - "CloseAll 方法"
  - "CloseDataSource 方法"
  - "消費者精靈產生的類別和方法"
  - "GetRowsetProperties 方法"
  - "方法 [C++], OLE DB 消費者精靈產生的"
  - "OLE DB 消費者, 精靈產生的類別和方法"
  - "OpenAll 方法"
  - "OpenDataSource 方法"
  - "OpenRowset 方法"
  - "精靈產生的類別和方法"
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 消費者精靈產生的方法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ATL OLE DB 消費者精靈和 MFC 應用程式會產生某些您應該瞭解的函式。  請注意某些方法在使用屬性的專案內的實作方式不同，因此有一些特殊狀況；每種狀況的說明如下。  如需檢視插入程式碼的詳細資訊，請參閱[偵錯插入程式碼](../Topic/How%20to:%20Debug%20Injected%20Code.md)。  
  
-   `OpenAll` 將會開啟資料來源、資料列集，若書籤可用也會開啟它們。  
  
-   `CloseAll` 會關閉所有開啟的資料列集，並釋放所有的命令執行。  
  
-   `OpenRowset` 是由 OpenAll 呼叫來開啟消費者的一或多個資料列集。  
  
-   `GetRowsetProperties` 會擷取資料列集屬性集合的指標，有了它就可以設定屬性。  
  
-   `OpenDataSource` 會使用您指定於 \[**資料連結內容**\] 對話方塊中的初始化字串來開啟資料來源。  
  
-   `CloseDataSource` 會以適當的方式關閉資料來源。  
  
## OpenAll 和 CloseAll  
  
```  
HRESULT OpenAll();   
void CloseAll();  
```  
  
 下列範例顯示當您重複地執行相同的命令時，呼叫 `OpenAll` 和 `CloseAll` 。  相較於 [CCommand::Close](../../data/oledb/ccommand-close.md) 內的程式碼範例，則顯示了呼叫 **Close** 和 `ReleaseCommand` 的不同作法，而不是 `CloseAll`。  
  
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
  
## 備註  
 請注意，如果您定義了 `HasBookmark` 方法，則 `OpenAll`  程式碼會設定 DBPROP\_IRowsetLocate 屬性，請確認只有在您的提供者支援該屬性時才這麼做。  
  
## OpenRowset  
  
```  
// OLE DB Template version:   
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);  
```  
  
 **OpenAll** 會呼叫此方法來開啟消費者內的一或多個資料列集。  通常，您不需要呼叫 `OpenRowset`，除非您想要使用多個資料來源、工作階段或資料錄集。  `OpenRowset` 是在命令或資料表類別標頭檔中宣告：  
  
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
  
 屬性將以不同的方式實作此方法。  此版本將接受一工作階段 \(Session\) 物件和一預設值為 db\_command 所指定命令字串的命令字串，不過您仍可傳入不同的資料。  請注意，如果您定義了 `HasBookmark` 方法，則 `OpenRowset`  程式碼將會設定 DBPROP\_IRowsetLocate 屬性，請確認您只有在提供者支援該屬性時才如此做。  
  
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
  
## GetRowsetProperties  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet);  
```  
  
 此方法可擷取資料列集之屬性集合的指標；您可使用此指標來設定屬性，例如 DBPROP\_IRowsetChange。  `GetRowsetProperties` 可用於使用者資料錄類別，如下所示。  您可修改此程式碼來設定額外的資料列集屬性：  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
## 備註  
 您不應定義全域的 `GetRowsetProperties` 方法，因為它可能與精靈定義的方法相衝突。  請注意這是您透過使用樣板和屬性專案取得的精靈產生方法；屬性並不會插入此程式碼。  
  
## OpenDataSource 和 CloseDataSource  
  
```  
HRESULT OpenDataSource();   
void CloseDataSource();  
```  
  
## 備註  
 精靈會定義方法 `OpenDataSource` 和 `CloseDataSource`，`OpenDataSource` 則會呼叫 [CDataSource::OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)。  
  
## 請參閱  
 [使用精靈建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)