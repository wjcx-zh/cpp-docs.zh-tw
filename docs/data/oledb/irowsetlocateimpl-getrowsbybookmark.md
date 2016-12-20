---
title: "IRowsetLocateImpl::GetRowsByBookmark | Microsoft Docs"
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
  - "IRowsetLocateImpl::GetRowsByBookmark"
  - "IRowsetLocateImpl.GetRowsByBookmark"
  - "GetRowsByBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRowsByBookmark 方法"
ms.assetid: 07906e42-3582-427e-812a-aa19791e3c56
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetLocateImpl::GetRowsByBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取至少一個符合指定書籤的資料行。  
  
## 語法  
  
```  
  
      STDMETHOD ( GetRowsByBookmark )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const DBBKMARK rgcbBookmarks[],  
   const BYTE* rgpBookmarks,  
   HROW rghRows[],  
   DBROWSTATUS* rgRowStatus[]   
);  
```  
  
#### 參數  
 `hReserved`  
 \[in\] 對應於 `hChapter` 參數中 [IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx)。  
  
 如需其他參數，請參閱《 *OLE DB 程式設計人員參考》的*[IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx) 。  
  
## 備註  
 書籤可以是您所定義或 OLE DB [標準書籤](https://msdn.microsoft.com/en-us/library/ms712954.aspx) 值 \(**DBBMK\_FIRST** 和 **DBBMK\_LAST**\)。  不變更資料指標位置。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetLocateImpl 類別](../../data/oledb/irowsetlocateimpl-class.md)   
 [IRowsetLocateImpl::GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)