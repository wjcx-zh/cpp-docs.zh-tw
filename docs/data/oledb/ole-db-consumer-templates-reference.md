---
title: "OLE DB 消費者樣板參考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-attr.db_param"
  - "vc-attr.db_column"
  - "vc-attr.db_accessor"
  - "vc-attr.db_command"
  - "vc-attr.db_table"
  - "vc.templates.ole"
  - "vc-attr.db_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 消費者樣板, 類別"
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 消費者樣板參考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 消費者樣板包含下列類別。  參考資料也包含在 [OLE DB 消費者樣板的巨集](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)主題。  
  
## 工作階段類別  
 [CDataConnection](../../data/oledb/cdataconnection-class.md)  
 管理與資料來源的連接。  這是建立用戶端一個有用的類別，因為它封裝必要的必須完成，連接到資料來源的物件 \(資料來源和工作階段\) 和某些工作。  
  
 [CDataSource](../../data/oledb/cdatasource-class.md)  
 會對應至 OLE DB 資料來源物件，表示連接是透過提供者和資料來源。  一或多個資料庫工作階段，為 `CSession` 物件中的每一個，在單一連結可能在執行。  
  
 [CEnumerator](../../data/oledb/cenumerator-class.md)  
 會對應至 OLE DB 列舉程式物件，以擷取可用資料來源的資料列集資訊。  
  
 [CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)  
 由 `CEnumerator` 列舉資料存取資料。  此資料列集包括資料來源和列舉值顯示從目前的列舉值。  
  
 [CSession](../../data/oledb/csession-class.md)  
 表示單一資料庫存取工作階段。  一或多個工作階段可以與每個 `CDataSource` 物件。  
  
## 存取子類別  
 [CAccessor](../../data/oledb/caccessor-class.md)  
 使用以靜態方式繫結至資料來源的資料錄。  當您知道資料來源的結構時，請使用這個存取子類別。  
  
 [CAccessorBase](../../data/oledb/caccessorbase-class.md)  
 所有存取子類別的基底類別。  
  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)  
 可以在執行階段建立存取子，根據資料列集的資料行資訊。  如果您不知道資料來源的結構，請使用這個類別擷取資料。  
  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)  
 可以使用的存取子，當命令類型不明。  藉由呼叫 `ICommandWithParameters` 介面取得參數資訊，因此，如果提供者支援介面。  
  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)  
 在不知道資料庫的基礎結構時，可讓您存取資料來源。  
  
 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)  
 類似於從資料存放區，但這個類別會要求資料存取的 `CDynamicStringAccessor` 當做 ANSI 字串資料。  
  
 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)  
 類似於從資料存放區，但這個類別會要求資料存取的 `CDynamicStringAccessor` 為 UNICODE 字串資料。  
  
 [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)  
 會處理資料行和命令參數的方法存取子。  這個類別，只要，提供者可以轉換成型別，您可以使用任何資料型別。  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 當您不要類別支援參數或輸出資料行時，可以使用做為樣板引數。  
  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)  
 類似於從資料存放區，但這個類別會將所有資料存取的 `CDynamicStringAccessor` 做為 XML 格式 \(標記\) 資料。  
  
## 資料列集類別  
 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md)  
 封裝資料列集及其關聯的存取子。  
  
 [CArrayRowset](../../data/oledb/carrayrowset-class.md)  
 使用陣列語法，用來存取資料列集的項目。  
  
 [CBulkRowset](../../data/oledb/cbulkrowset-class.md)  
 用來藉由擷取具有單一呼叫的多行控制代碼擷取和操作執行大量。  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 如果命令不傳回資料列集，可當做樣板引數。  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md)  
 用於結構描述資料列集指定限制。  
  
 [CRowset](../../data/oledb/crowset-class.md)  
 用來管理，設定和擷取資料列集資料。  
  
 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)  
 傳回 `ISequentialStream` 物件 \(而不是資料列集;然後使用 **Read** 方法以擷取 XML 格式的資料。\(SQL Server 2000 進行格式化;請注意這個功能只和 SQL Server 2000 一起使用\)。  
  
 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)  
 提供 `IRowsetNotify`的假的實作，以 `IRowsetNotify` 方法的 `OnFieldChange`、 `OnRowChange`和 `OnRowsetChange`空函式。  
  
 [結構描述資料列集類別及 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)  
  
 OLE DB 樣板提供您對應至 OLE DB 結構描述資料列集的類別。  
  
## 命令類別  
 [CCommand](../../data/oledb/ccommand-class.md)  
 用來設定和執行以參數的 OLE DB 命令。  只開啟簡單資料列集，請使用 `CTable` 。  
  
 [CMultipleResults](../../data/oledb/cmultipleresults-class.md)  
 當做樣板引數為 `CCommand` 範本，當您想要命令時處理多個結果集。  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 當做樣板引數為樣板類別，例如 `CCommand` 和 `CTable`，並存取子類別引數。  如果不要類別支援參數或輸出行，請使用 `CNoAccessor` 。  
  
 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)  
 當做樣板引數為 `CCommand` 範本，當您想要命令處理單一資料列集。  `CNoMultipleResults` 是樣板引數的預設值。  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 當做樣板引數為 `CCommand` 或 `CTable` ，如果命令或資料表不傳回資料列集。  
  
 [CTable](../../data/oledb/ctable-class.md)  
 用來存取簡單資料列集沒有參數。  
  
## 屬性類別  
 [CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)  
 用來藉由陣列消費者想要屬性資訊的屬性 ID。  屬性所屬的屬性集合。  
  
 [CDBPropSet](../../data/oledb/cdbpropset-class.md)  
 用來設定提供者的屬性。  
  
## 書籤類別  
 [CBookmark](../../data/oledb/cbookmark-class.md)  
 做為索引以存取資料列集。  
  
## 錯誤類別  
 [CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)  
 用來擷取 OLE DB 錯誤資訊。  
  
## 請參閱  
 [OLE DB 提供者樣板參考](../../data/oledb/ole-db-provider-templates-reference.md)   
 [OLE DB 樣板](../../data/oledb/ole-db-templates.md)