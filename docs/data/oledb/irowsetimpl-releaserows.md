---
title: "IRowsetImpl::ReleaseRows | Microsoft Docs"
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
  - "ATL.IRowsetImpl.ReleaseRows"
  - "ReleaseRows"
  - "IRowsetImpl::ReleaseRows"
  - "ATL::IRowsetImpl::ReleaseRows"
  - "IRowsetImpl.ReleaseRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseRows 方法"
ms.assetid: e4d47be8-8ebf-485b-b1e9-df13e4c8ee8d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::ReleaseRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

釋放資料列。  
  
## 語法  
  
```  
  
      STDMETHOD( ReleaseRows )(  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWOPTIONS rgRowOptions[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[]   
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[IRowset::ReleaseRows](https://msdn.microsoft.com/en-us/library/ms719771.aspx) 。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)