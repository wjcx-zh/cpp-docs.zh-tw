---
title: "IRowsetImpl::RefRows | Microsoft Docs"
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
  - "ATL::IRowsetImpl::RefRows"
  - "ATL.IRowsetImpl.RefRows"
  - "IRowsetImpl.RefRows"
  - "RefRows"
  - "IRowsetImpl::RefRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RefRows 方法"
ms.assetid: 1c048a2a-65dc-4bba-9c81-a23c0dc249c8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::RefRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) 和 [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md) 或加入或釋放參考計數重新命名現有的資料列控制代碼。  
  
## 語法  
  
```  
  
      HRESULT RefRows(  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[],  
   BOOL bAdd   
);  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考* 的 [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) 。  
  
## 傳回值  
 標準 `HRESULT` 值。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)   
 [CSimpleRow 類別](../../data/oledb/csimplerow-class.md)