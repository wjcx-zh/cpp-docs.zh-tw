---
title: "CMyProviderSession (MyProviderSess.H) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmyprovidersession
- myprovidersess.h
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4ffb1a0ca8e9a2cd5b90d33c21423beb0969a4f4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cmyprovidersession-myprovidersessh"></a>CMyProviderSession (MyProviderSess.H)
MyProviderSess.H 包含宣告和實作的 OLE DB 工作階段物件。 資料來源物件建立的工作階段物件，並代表消費者和提供者之間的交談。 多個同時進行的工作階段可以有一個資料來源開啟。 繼承清單`CMyProviderSession`遵循：  
  
```cpp
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
  
 工作階段物件會繼承**IGetDataSource**， `IOpenRowset`， **ISessionProperties**，和**IDBCreateCommand**。 **IGetDataSource**介面可讓工作階段擷取資料來源建立它。 這是您需要取得屬性，從您建立的資料來源或資料來源所提供的其他資訊時相當實用。 **ISessionProperties**介面會處理工作階段的所有屬性。 `IOpenRowset`和**IDBCreateCommand**介面可用來執行資料庫工作。 如果提供者支援的命令，它會實作**IDBCreateCommand**介面。 它用來建立可執行命令的命令物件。 提供者一律會實作`IOpenRowset`物件。 它用來產生簡單的資料列集提供者。 它是預設的資料列集 (例如， `"select * from mytable"`) 從提供者。  
  
 精靈也會產生工作階段的三個類別： `CMyProviderSessionColSchema`， `CMyProviderSessionPTSchema`，和`CMyProviderSessionTRSchema`。 這些工作階段會用於結構描述資料列。 結構描述資料列集可讓要傳回給取用者的中繼資料，而不需要重新執行查詢或擷取資料的取用者的提供者。 擷取中繼資料會遠比探索提供者功能更快。  
  
 OLE DB 規格要求提供者實作**IDBSchemaRowset**介面支援三個結構描述資料列集類型： **DBSCHEMA_COLUMNS**， **DBSCHEMA_PROVIDER_TYPES**，和`DBSCHEMA_TABLES`。 精靈會產生每個結構描述資料列集的實作。 每個精靈所產生的類別包含`Execute`方法。 在這個`Execute`方法，您可以傳回資料給提供者所支援相關資料表、 資料行和資料類型。 這項資料通常是在編譯時期已知的。  
  
## <a name="see-also"></a>請參閱  
 [提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)