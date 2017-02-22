---
title: "CBulkRowset 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CBulkRowset"
  - "ATL.CBulkRowset"
  - "ATL::CBulkRowset<TAccessor>"
  - "CBulkRowset"
  - "ATL.CBulkRowset<TAccessor>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBulkRowset 類別"
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CBulkRowset 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取和操作資料列資料運作大量在擷取具有單一呼叫的多行控制碼旁邊。  
  
## 語法  
  
```  
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
#### 參數  
 `TAccessor`  
 存取子類別。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/cbulkrowset-addrefrows.md)|將參考次數 \(Reference Count\)。|  
|[CBulkRowset](../../data/oledb/cbulkrowset-cbulkrowset.md)|建構函式。|  
|[MoveFirst](../../data/oledb/cbulkrowset-movefirst.md)|擷取資料的第一行，如果需要，執行新的大量擷取。|  
|[MoveLast](../../data/oledb/cbulkrowset-movelast.md)|移至最後一行。|  
|[MoveNext](../../data/oledb/cbulkrowset-movenext.md)|擷取資料的下一行。|  
|[MovePrev](../../data/oledb/cbulkrowset-moveprev.md)|移至上一行。|  
|[MoveToBookmark](../../data/oledb/cbulkrowset-movetobookmark.md)|擷取書籤指示資料列或資料行在該書籤的指定位移。|  
|[MoveToRatio](../../data/oledb/cbulkrowset-movetoratio.md)|擷取在資料列集的分數位置開始資料列。|  
|[ReleaseRows](../../data/oledb/cbulkrowset-releaserows.md)|調整目前行 \(**m\_nCurrentRow**\) 為零和釋放所有資料行。|  
|[SetRows](../../data/oledb/cbulkrowset-setrows.md)|設定資料列數的呼叫中擷取的控制代碼。|  
  
## 範例  
 下列範例示範 `CBulkRowset` 類別的用法。  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/CPP/cbulkrowset-class_1.cpp)]  
  
## 需求  
 **Header:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)