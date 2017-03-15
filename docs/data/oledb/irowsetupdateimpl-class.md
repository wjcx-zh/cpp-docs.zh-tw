---
title: "IRowsetUpdateImpl 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetUpdateImpl"
  - "ATL.IRowsetUpdateImpl"
  - "ATL::IRowsetUpdateImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetUpdateImpl 類別"
  - "提供者, 可更新的"
  - "可更新的提供者, 延後更新"
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IRowsetUpdateImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) 介面的 OLE DB 樣板實作。  
  
## 語法  
  
```  
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  
class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass  
>  
```  
  
#### 參數  
 `T`  
 衍生自 `IRowsetUpdateImpl`的類別。  
  
 `Storage`  
 使用者資料錄。  
  
 `UpdateArray`  
 包含快取的資料更新的陣列資料列集。  
  
 `RowClass`  
 **HROW**的儲存格。  
  
 `MapClass`  
 所有資料列控制代碼的儲存格由提供者保留了。  
  
## 成員  
  
### 介面方法 \(使用與 IRowsetChange\)  
  
|||  
|-|-|  
|[SetData](../../data/oledb/irowsetupdateimpl-setdata.md)|將一或多個資料行的資料值。|  
  
### 介面方法 \(使用與 IRowsetUpdate\)  
  
|||  
|-|-|  
|[GetOriginalData](../../data/oledb/irowsetupdateimpl-getoriginaldata.md)|從資料來源取得資料最近傳送至或衍生，忽略暫止的變更。|  
|[GetPendingRows](../../data/oledb/irowsetupdateimpl-getpendingrows.md)|傳回具有暫止變更的資料行清單。|  
|[GetRowStatus](../../data/oledb/irowsetupdateimpl-getrowstatus.md)|傳回指定資料行狀態。|  
|[復原](../../data/oledb/irowsetupdateimpl-undo.md)|移除資料列的變更，自上次擷取或 Update。|  
|[更新](../../data/oledb/irowsetupdateimpl-update.md)|傳輸所做的任何變更時，自上次擷取或 Update。|  
  
### 實作方法 \(回呼\)  
  
|||  
|-|-|  
|[IsUpdateAllowed](../../data/oledb/irowsetupdateimpl-isupdateallowed.md)|用來檢查安全性，完整性，並且在允許更新之前發生。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_mapCachedData](../../data/oledb/irowsetupdateimpl-m-mapcacheddata.md)|包含延後作業的原始資料。|  
  
## 備註  
 因為中的一切其中也在此適用，您應先閱讀及了解 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)的資料。  您在設定資料也應該讀取 `OLE``DB``Programmer's``Reference` 的第 6 章。  
  
 `IRowsetUpdateImpl` 實作 OLE DB `IRowsetUpdate` 介面，可讓消費者延遲用 `IRowsetChange` 所做的變更傳送至資料來源並在傳送前復原變更。  
  
> [!IMPORTANT]
>  強烈建議您先實作提供者閱讀下列文件:  
  
-   [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)  
  
-   `OLE` `DB` `Programmer's` `Reference`的第 6 章  
  
-   請參閱 `RUpdateRowset` 類別如何使用 UpdatePV 範例  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)