---
title: "IRowsetImpl::AddRefRows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetImpl::AddRefRows"
  - "AddRefRows"
  - "IRowsetImpl.AddRefRows"
  - "ATL::IRowsetImpl::AddRefRows"
  - "ATL.IRowsetImpl.AddRefRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRefRows 方法"
ms.assetid: adc0989b-7592-432e-82d9-df4445431531
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::AddRefRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將參考次數 \(Reference Count\) 加入至現有的資料列控制代碼。  
  
## 語法  
  
```  
  
      STDMETHOD( AddRefRows )(  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[]   
);  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考* 的 [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) 。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)   
 [IRowsetImpl::GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)   
 [IRowsetImpl::ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)