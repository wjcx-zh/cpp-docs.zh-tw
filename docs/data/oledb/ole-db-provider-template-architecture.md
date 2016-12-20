---
title: "OLE DB 提供者樣板架構 | Microsoft Docs"
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
  - "架構 [C++], OLE DB 提供者"
  - "OLE DB [C++], 物件模型"
  - "OLE DB 提供者樣板, 物件模型"
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 提供者樣板架構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## 資料來源和工作階段  
 OLE DB 提供者架構包含一個資料來源物件和一或多個工作階段 \(Session\)。  資料來源物件為每個提供者都必須執行個體化的初始物件。  當消費者應用程式需要資料時，它會同時建立資料來源物件來啟動提供者。  該資料來源物件會建立一個讓消費者用來連接至資料來源物件的工作階段物件 \(使用 **IDBCreateSession** 介面\)。  ODBC 程式設計人員可將資料來源物件視同 **HENV**，而將工作階段物件則視為 **HDBC**。  
  
 ![提供者架構](../../data/oledb/media/vc4twb1.png "vc4TWB1")  
  
 OLE DB 樣板可搭配 OLE DB 提供者精靈所建立的原始程式檔 \(Source File\)，實作一個資料來源物件。  工作階段是對應至 OLE DB **TSession** 的物件。  
  
## 強制項和選擇項介面  
 OLE DB 提供者樣板提供您所有必要介面的預先封裝實作。  OLE DB 會替多個物件類型定義了強制項和選擇項介面：  
  
-   [資料來源](../../data/oledb/data-source-object-interfaces.md)  
  
-   [工作階段](../../data/oledb/session-object-interfaces.md)  
  
-   [資料列集](../../data/oledb/rowset-object-interfaces.md)  
  
-   [命令](../../data/oledb/command-object-interfaces.md)  
  
-   [異動](../../data/oledb/transaction-object-interfaces.md)  
  
 請注意，OLE DB 提供者樣板並不會實作資料列和儲存物件 \(Storage Object\)。  
  
 下表根據 [OLE DB 2.6 SDK 文件](https://msdn.microsoft.com/en-us/library/ms722784.aspx)，列出上列物件的強制項和選擇項介面。  
  
|元件|介面|Comment|  
|--------|--------|-------------|  
|[資料來源](../../data/oledb/data-source-object-interfaces.md) \([CDataSource](../../data/oledb/cdatasource-class.md)\)|\[強制\] **IDBCreateSession**<br /><br /> \[強制\] **IDBInitialize**<br /><br /> \[強制\] `IDBProperties`<br /><br /> \[強制\] `IPersist`<br /><br /> \[選擇項\] **IConnectionPointContainer**<br /><br /> \[選擇項\] **IDBAsynchStatus**<br /><br /> \[選擇項\] **IDBDataSourceAdmin**<br /><br /> \[選擇項\] **IDBInfo**<br /><br /> \[選擇項\] `IPersistFile`<br /><br /> \[選擇項\] **ISupportErrorInfo**|自消費者連接至提供者。  用來指定連接屬性的物件，例如，使用者 ID、密碼和資料來源名稱 \(Data Source Name\)。  物件也可用來管理資料來源 \(建立、更新、刪除、表格等等\)。|  
|[工作階段](../../data/oledb/session-object-interfaces.md) \([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md)\)|\[強制\] **IGetDataSource**<br /><br /> \[強制\] `IOpenRowset`<br /><br /> \[強制\] **ISessionProperties**<br /><br /> \[選擇項\] **IAlterIndex**<br /><br /> \[選擇項\] **IAlterTable**<br /><br /> \[選擇項\] **IBindResource**<br /><br /> \[選擇項\] **ICreateRow**<br /><br /> \[選擇項\] **IDBCreateCommand**<br /><br /> \[選擇項\] **IDBSchemaRowset**<br /><br /> \[選擇項\] **IIndexDefinition**<br /><br /> \[選擇項\] **ISupportErrorInfo**<br /><br /> \[選擇項\] **ITableCreation**<br /><br /> \[選擇項\] **ITableDefinition**<br /><br /> \[選擇項\] **ITableDefinitionWithConstraints**<br /><br /> \[選擇項\] **ITransaction**<br /><br /> \[選擇項\] **ITransactionJoin**<br /><br /> \[選擇項\] **ITransactionLocal**<br /><br /> \[選擇項\] **ITransactionObject**|工作階段物件代表消費者和提供者之間的單一轉換。  有點類似 ODBC **HSTMT**，因為可以有很多同時作用的工作階段。<br /><br /> 工作階段物件是取得 OLE DB 功能的主要連結。  若要取得命令、交易或資料列集物件，您可瀏覽一遍工作階段物件。|  
|[資料列集](../../data/oledb/rowset-object-interfaces.md) \([CRowset](../../data/oledb/crowset-class.md)\)|\[強制\] `IAccessor`<br /><br /> \[強制\] `IColumnsInfo`<br /><br /> \[強制\] **IConvertType**<br /><br /> \[強制\] `IRowset`<br /><br /> \[強制\] `IRowsetInfo`<br /><br /> \[選擇項\] **IChapteredRowset**<br /><br /> \[選擇項\] **IColumnsInfo2**<br /><br /> \[選擇項\] **IColumnsRowset**<br /><br /> \[選擇項\] **IConnectionPointContainer**<br /><br /> \[選擇項\] **IDBAsynchStatus**<br /><br /> \[選擇項\] **IGetRow**<br /><br /> \[選擇項\] `IRowsetChange`<br /><br /> \[選擇項\] **IRowsetChapterMember**<br /><br /> \[選擇項\] **IRowsetCurrentIndex**<br /><br /> \[選擇項\] **IRowsetFind**<br /><br /> \[選擇項\] **IRowsetIdentity**<br /><br /> \[選擇項\] **IRowsetIndex**<br /><br /> \[選擇項\] `IRowsetLocate`<br /><br /> \[選擇項\] **IRowsetRefresh**<br /><br /> \[選擇項\] `IRowsetScroll`<br /><br /> \[選擇項\] `IRowsetUpdate`<br /><br /> \[選擇項\] **IRowsetView**<br /><br /> \[選擇項\] **ISupportErrorInfo**<br /><br /> \[選擇項\] **IRowsetBookmark**|資料列集物件代表來自資料來源的資料。  此物件負責該資料的繫結，和任何的基本資料操作 \(更新、擷取、移動和其他作業\)。  您永遠會有包含和管理資料的資料列集物件。|  
|[命令](../../data/oledb/command-object-interfaces.md) \([CCommand](http://msdn.microsoft.com/zh-tw/52bef5da-c1a0-4223-b4e6-9e464b6db409)\)|\[強制\] `IAccessor`<br /><br /> \[強制\] `IColumnsInfo`<br /><br /> \[強制\] `ICommand`<br /><br /> \[強制\] **ICommandProperties**<br /><br /> \[強制\] `ICommandText`<br /><br /> \[強制\] **IConvertType**<br /><br /> \[選擇項\] **IColumnsRowset**<br /><br /> \[選擇項\] **ICommandPersist**<br /><br /> \[選擇項\] **ICommandPrepare**<br /><br /> \[選擇項\] `ICommandWithParameters`<br /><br /> \[選擇項\] **ISupportErrorInfo**<br /><br /> \[選擇項\] **ICommandStream**|處理資料作業的命令物件，例如查詢。  它可以處理參數型或非參數型陳述式。<br /><br /> 命令物件也負責處理參數和輸出資料行的繫結。  繫結是一個包含資料列集資料行擷取方式之相關資訊的結構。  它包含了序數、資料型別、長度和狀態的資訊。|  
|[交易](../../data/oledb/transaction-object-interfaces.md) \(選擇項\)|\[強制\] **IConnectionPointContainer**<br /><br /> \[強制\] **ITransaction**<br /><br /> \[選擇項\] **ISupportErrorInfo**|交易物件定義資料來源內的原子單位，並決定這些工作單位彼此間的關係。  OLE DB 提供者樣板並未直接支援這個物件 \(也就是您建立自己的物件\)。|  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [屬性對應](../../data/oledb/property-maps.md)  
  
-   [使用者資料錄](../../data/oledb/user-record.md)  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB Interfaces](https://msdn.microsoft.com/en-us/library/ms709709.aspx)