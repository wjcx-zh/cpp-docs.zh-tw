---
title: "CMyProviderSession (MyProviderSess.H) | Microsoft Docs"
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
  - "cmyprovidersession"
  - ""myprovidersess.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MyProviderSess.H 中的 CMyProviderSession 類別"
  - "OLE DB 提供者, 精靈產生的檔案"
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderSession (MyProviderSess.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MyProviderSess.H 包含 OLE DB 工作階段物件的宣告和實作。  資料來源物件會建立工作階段物件，並代表在消費者和提供者之間的交談。  多個同時的工作階段可針對一個資料來源開啟。  `CMyProviderSession` 的繼承 \(Inheritance\) 清單如下所示：  
  
```  
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSession  
class ATL_NO_VTABLE CMyProviderSession :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IGetDataSourceImpl<CMyProviderSession>,  
   public IOpenRowsetImpl<CMyProviderSession>,  
   public ISessionPropertiesImpl<CMyProviderSession>,  
   public IObjectWithSiteSessionImpl<CMyProviderSession>,  
   public IDBSchemaRowsetImpl<CMyProviderSession>,  
   public IDBCreateCommandImpl<CMyProviderSession, CMyProviderCommand>  
```  
  
 工作階段物件繼承自 **IGetDataSource**、`IOpenRowset`、**ISessionProperties** 和 **IDBCreateCommand**。  **IGetDataSource** 介面可讓工作階段擷取建立它的資料來源。  若需取得建立資料來源的屬性，或取得資料來源所提供的其他資訊，這種介面就十分實用。  **ISessionProperties** 介面可處理工作階段的所有屬性。  `IOpenRowset` 和 **IDBCreateCommand** 介面可用來進行資料庫工作。  如果提供者支援命令，就會實作 **IDBCreateCommand** 介面。  這個介面可用來建立可執行命令的命令物件。  提供者一定會實作 `IOpenRowset` 物件。  這個物件會用來從提供者產生簡單的資料列集 \(Rowset\)。  它是提供者的預設資料列集 \(例如，`"select * from mytable"`\)。  
  
 精靈也會產生三個工作階段類別：`CMyProviderSessionColSchema`、`CMyProviderSessionPTSchema` 和 `CMyProviderSessionTRSchema`。  這些工作階段將用於結構描述 \(Schema\) 資料列集。  結構描述資料列集可讓提供者將中繼資料 \(Metadata\) 傳回至消費者，而不需要消費者執行查詢或擷取資料。  擷取中繼資料的速度遠比發現提供者功能來得快。  
  
 OLE DB 規格中要求實作 **IDBSchemaRowset** 介面的提供者需支援三個結構描述資料列集型別：**DBSCHEMA\_COLUMNS**、**DBSCHEMA\_PROVIDER\_TYPES** 和 `DBSCHEMA_TABLES`。  精靈可為每個結構描述資料列集產生實作。  精靈所產生的每個類別都包含 `Execute` 方法。  在此 `Execute` 方法中，您可將資料表、資料行和所支援資料型別的相關資料傳給提供者。  此資料通常是在編譯時間得知。  
  
## 請參閱  
 [提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)