---
title: "CRowset 類別 | Microsoft Docs"
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
  - "ATL.CRowset<TAccessor>"
  - "CRowset"
  - "ATL::CRowset"
  - "ATL::CRowset<TAccessor>"
  - "ATL.CRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRowset 類別"
ms.assetid: b0228a90-b8dd-47cc-b397-8d4c15c1e7f4
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 OLE DB 資料列集物件和數個相關介面且提供資料列集資料操作方法。  
  
## 語法  
  
```  
template <class TAccessor = CAccessorBase>  
class CRowset  
```  
  
#### 參數  
 `TAccessor`  
 存取子類別  預設為 `CAccessorBase`。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/crowset-addrefrows.md)|增加與目前資料列相關的參考次數 \(Reference Count\)。|  
|[關閉](../../data/oledb/crowset-close.md)|釋放資料列和目前的 `IRowset` 介面。|  
|[Compare](../../data/oledb/crowset-compare.md)|使用 [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx) 比較兩個書籤。|  
|[CRowset](../../data/oledb/crowset-crowset.md)|建立新的 `CRowset` 物件以及關連 \(選擇性\) 當做參數提供的 **IRowset** 介面。|  
|[Delete](../../data/oledb/crowset-delete.md)|使用 [IRowsetChange: DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx) 從資料列集刪除資料行。|  
|[FindNextRow](../../data/oledb/crowset-findnextrow.md)|尋找下一個符合的資料列，在指定的書籤後。|  
|[GetApproximatePosition](../../data/oledb/crowset-getapproximateposition.md)|傳回與書籤對應的資料列的大約位置。|  
|[GetData](../../data/oledb/crowset-getdata.md)|從資料列集的資料列複本擷取資料。|  
|[GetDataHere](../../data/oledb/crowset-getdatahere.md)|從指定的緩衝區擷取資料。|  
|[GetOriginalData](../../data/oledb/crowset-getoriginaldata.md)|擷取最近擷取或傳送至資料來源的資料，忽略暫止的變更。|  
|[GetRowStatus](../../data/oledb/crowset-getrowstatus.md)|傳回所有資料列狀態。|  
|[Insert](../../data/oledb/crowset-insert.md)|使用 [IRowsetChange: InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx) 建立和插入新資料列。|  
|[IsSameRow](../../data/oledb/crowset-issamerow.md)|將目前的與指定的資料列相比較。|  
|[MoveFirst](../../data/oledb/crowset-movefirst.md)|將下一個擷取位置重新放置在其初始位置。|  
|[MoveLast](../../data/oledb/crowset-movelast.md)|移至最後一個記錄。|  
|[MoveNext](../../data/oledb/crowset-movenext.md)|從下一個連續行或在下一行之外的指定數字位置擷取資料。|  
|[MovePrev](../../data/oledb/crowset-moveprev.md)|移至上一個記錄。|  
|[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)|擷取書籤指示資料列或資料行中的指定位移從該書籤。|  
|[MoveToRatio](../../data/oledb/crowset-movetoratio.md)|擷取在資料列集的分數位置開始資料列。|  
|[ReleaseRows](../../data/oledb/crowset-releaserows.md)|呼叫 [IRowset::ReleaseRows](https://msdn.microsoft.com/en-us/library/ms719771.aspx) 以釋放目前資料列控制代碼。|  
|[SetData](../../data/oledb/crowset-setdata.md)|[CRowset::SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx) 可以在資料列的一個或多個資料行中設定資料值。|  
|[復原](../../data/oledb/crowset-undo.md)|自上次擷取或 [更新](../../data/oledb/crowset-update.md) 移除所做的任何變更。|  
|[更新](../../data/oledb/crowset-update.md)|傳送目前資料列自上次擷取或更新呼叫之後任何暫止的變更。|  
|[UpdateAll](../../data/oledb/crowset-updateall.md)|傳輸自上次擷取或更新對所有的行進行的所有暫止變更。|  
  
## 備註  
 在 OLE DB，資料列集是程式用以設定和擷取資料的物件。  
  
 這個類別不會具現化，而是會當做樣板參數給 `CTable` 或 `CCommand` \(`CRowset` 為預設值\)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [DBViewer 範例](../../top/visual-cpp-samples.md)   
 [MultiRead 範例](../../top/visual-cpp-samples.md)   
 [MultiRead 屬性範例](../../top/visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)