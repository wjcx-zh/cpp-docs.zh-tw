---
title: "CAccessorRowset 類別 | Microsoft Docs"
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
  - "CAccessorRowset"
  - "ATL.CAccessorRowset"
  - "ATL::CAccessorRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessorRowset 類別"
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorRowset 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝資料列集及其關聯的存取子單一類別的。  
  
## 語法  
  
```  
template <   
   class TAccessor = CNoAccessor,    
   template <typename T> class TRowset = CRowset    
>  
class CAccessorRowset :   
   public TAccessor,    
   public TRowset<TAccessor>  
```  
  
#### 參數  
 `TAccessor`  
 存取子類別。  
  
 `TRowset`  
 資料列集類別。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[Bind](../../data/oledb/caccessorrowset-bind.md)|建立繫結 \(使用 **bBind** 時指定為 false 以 [CCommand::Open](../../data/oledb/ccommand-open.md)為單位\)。|  
|[CAccessorRowset](../../data/oledb/caccessorrowset-caccessorrowset.md)|建構函式。|  
|[關閉](../../data/oledb/caccessorrowset-close.md)|關閉所有資料列集和存取子。|  
|[FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md)|釋放需要釋放目前記錄的所有資料列。|  
|[GetColumnInfo](../../data/oledb/caccessorrowset-getcolumninfo.md)|實作 [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)。|  
  
## 備註  
 類別處理 `TAccessor` 存取子。  *TRowset* 類別處理資料列集。  
  
## 需求  
 **Header:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)