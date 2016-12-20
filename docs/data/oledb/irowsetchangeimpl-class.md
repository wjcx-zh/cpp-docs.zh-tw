---
title: "IRowsetChangeImpl 類別 | Microsoft Docs"
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
  - "ATL::IRowsetChangeImpl"
  - "IRowsetChangeImpl"
  - "ATL.IRowsetChangeImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetChangeImpl 類別"
  - "提供者, 可更新的"
  - "可更新的提供者, 立即更新"
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetChangeImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) 介面的 OLE DB 樣板實作 OLE DB 規格。  
  
## 語法  
  
```  
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >   
>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
#### 參數  
 `T`  
 衍生自 `IRowsetChangeImpl` 的類別。  
  
 `Storage`  
 使用者資料錄  
  
 `BaseInterface`  
 介面的基底實作，像是`IRowsetChange`。  
  
 `RowClass`  
 資料列控制代碼的儲存格。  
  
 `MapClass`  
 由提供者保留的所有資料列控制代碼的儲存單位。  
  
## 成員  
  
### 介面方法 \(使用 IRowsetChange\)  
  
|||  
|-|-|  
|[DeleteRows](../../data/oledb/irowsetchangeimpl-deleterows.md)|刪除列集合中的列。|  
|[InsertRow](../../data/oledb/irowsetchangeimpl-insertrow.md)|將資料列插入至資料列集。|  
|[SetData](../../data/oledb/irowsetchangeimpl-setdata.md)|一個或多個資料行中設定資料值。|  
  
### 實作方法 \(回呼\)  
  
|||  
|-|-|  
|[FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)|由做資料提供者的 Overidden 對它的存放區。|  
  
## 備註  
 這個介面會直接寫入作業負責資料存放區。「直接」是表示使用者 \(使用消費者\) 的人做任何變更，這些變更立即傳送至資料存放區 \(和無法取消\)。  
  
 `IRowsetChangeImpl` 實作 OLE DB `IRowsetChange` 介面，以便在現有資料列中，刪除資料行和插入新資料列的更新資料行的值。  
  
 OLE DB 樣板實作支援任何基底方法 \(`SetData`、 `InsertRow`和 `DeleteRows`\)。  
  
> [!IMPORTANT]
>  強烈建議您先實作提供者閱讀下列文件:  
  
-   [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)  
  
-   *OLE DB Programmer's Reference*的第 6 章  
  
-   請參閱 `RUpdateRowset` 類別如何使用 UpdatePV 範例  
  
## 需求  
 **Header:**  atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)