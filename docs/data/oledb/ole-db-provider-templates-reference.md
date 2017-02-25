---
title: "OLE DB 提供者樣板參考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.templates.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供者樣板"
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OLE DB 提供者樣板參考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

類別和介面 OLE DB 提供者樣板可分為下列分類。  參考資料也包含 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)的相關資訊。  
  
 類別使用下列命名慣例:與這個樣式 **IWidgetImpl** 的類別名稱會提供介面 **IWidget**的實作。  
  
## 工作階段類別  
 [IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)  
 從資料來源物件中建立新工作階段，並傳回這個新建立的工作階段所要求的介面。  資料來源物件中的必要的介面。  
  
 [ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)  
 實作工作階段屬性呼叫靜態函式所定義的屬性集對應。  在您的工作階段類別應該指定屬性集對應。  在工作階段中需要的介面。  
  
## 資料列集類別  
 [CRowsetImpl](../../data/oledb/crowsetimpl-class.md)  
  
 提供標準 OLE DB 資料列集實作，而不需要許多實作介面的多重繼承。  您必須提供實作的唯一方法是 **Execute**。  
  
 [CSimpleRow](../../data/oledb/csimplerow-class.md)  
 資料列控制代碼提供的預設實作\(在 `IRowsetImpl` 類別被使用\)。  資料列控制代碼在邏輯上是結果資料行的唯一的標記。  `IRowsetImpl` 會在 `IRowsetImpl::GetNextRows`要求的每個資料列的新 `CSimpleRow` 。  
  
 [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)  
 OLE DB 需要提供者實作 **HACCESSOR**，是標記為陣列 **DBBINDING** 結構。  提供 **HACCESSOR**是 **BindType** 結構的位址的。  資料列集和命令的強制轉型。  
  
 [IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)  
 提供者中所定義的靜態函式的委派對應。  在資料列集和命令的需要的介面。  
  
 [IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)  
 提供型別轉換的可用性的資訊列在命令或。  命令、資料列集和索引資料列集的強制轉型。  建立 **IConvertTypeImpl** 委派傳遞至轉換 OLE DB 提供的實作介面的物件。  
  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)  
 實作 **IDBSchemaRowset** 介面和樣板化建立者函式 `CreateSchemaRowset`。  
  
 [IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)  
 開啟並傳回含有來自單一基底資料表或索引的所有資料行的資料列集。  工作階段物件的必要的介面。  
  
 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)  
 實作 OLE DB [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) 介面，以便在現有資料列中，刪除資料行和插入新資料列的更新資料行的值。  
  
 [IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)  
 這個類別會從 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) 繼承並覆寫 [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)。  執行函式和 `IRowsetCreatorImpl` ，而且啟用 OLE DB 屬性 `IObjectWithSite`**DBPROPCANSCROLLBACKWARDS** 和 **DBPROPCANFETCHBACKWARDS**。  
  
 [IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)  
 實作 **IRowsetIdentity** 介面，可讓您比較這兩個資料行是相同的。  
  
 [IRowsetImpl](../../data/oledb/irowsetimpl-class.md)  
 提供 `IRowset` 介面的實作，做為基礎資料列集介面。  
  
 [IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)  
 實作在您的命令類別使用 屬性集對應 定義資料列集屬性。  在資料列集的強制介面。  
  
 [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)  
 實作 OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) 介面，從資料列集擷取任意資料列。  若要支援在資料列集的 OLE DB 書籤，使資料列集繼承這個類別。  
  
 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)  
 實作廣播功能，以通知在 **IID\_IRowsetNotify** 連接點上的接聽程式關於資料列集內容的變更。  處理告知的消費者實作 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) 並註冊該連接點。  
  
 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)  
 實作 OLE DB [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) 介面，可讓消費者延遲用 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) 所做的變更傳送至資料來源並在傳送前復原變更。  
  
## 命令類別  
 [ICommandImpl](../../data/oledb/icommandimpl-class.md)  
 提供 `ICommand` 介面的實作。  這個介面不是可見的，則為，而是由 **ICommandTextImpl**處理。  在命令物件上必須的介面。  
  
 [ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)  
 `BEGIN_PROPSET_MAP` 巨集定義的靜態函式提供 **ICommandProperties** 介面的實作。  命令的強制轉型。  
  
 [ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)  
 設定、儲存和傳回命令文字。  命令的強制轉型。  
  
 [IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)  
 建立從工作階段物件的新命令並傳回在新建立的命令的要求的介面。  在工作階段物件的選擇性介面。  
  
 其他命令類別是 `IColumnsInfoImpl` 和 `IAccessorImpl`，描述在上方資料列集類別部分。  
  
## 資料來源類別  
 [IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)  
 建立和刪除與消費者的連接。  資料來源物件的強制介面並列舉值的選擇性介面。  
  
 [IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)  
 `IDBProperties` 是資料來源物件中需要的介面和列舉值的選擇性介面。  不過，則為，如果列舉值公開 **IDBInitialize**，它必須公開 `IDBProperties` \(在資料來源的屬性\)。  
  
 [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)  
 取得的介面指標資料來源物件。  在工作階段中需要的介面。  
  
## 其他類別  
 [CUtlProps](../../data/oledb/cutlprops-class.md)  
 實作各種 OLE DB 屬性介面的屬性 \(例如， `IDBProperties`、 `IRowsetInfo`和 **ISessionProperties**\)。  
  
 [IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)  
  
 實作 OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 介面，加入資料錄並擷取資料錄從資料成員。  
  
## 請參閱  
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [OLE DB 樣板](../../data/oledb/ole-db-templates.md)