---
title: "IRowsetUpdateImpl::Undo | Microsoft Docs"
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
  - "ATL.IRowsetUpdateImpl.Undo"
  - "ATL::IRowsetUpdateImpl::Undo"
  - "IRowsetUpdateImpl::Undo"
  - "IRowsetUpdateImpl.Undo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Undo 方法"
ms.assetid: f3dc7764-050c-4322-9b2f-9ca772a0fb88
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetUpdateImpl::Undo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

移除資料列的變更，自上次擷取或 Update。  
  
## 語法  
  
```  
  
      STDMETHOD ( Undo )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[ ],  
   DBCOUNTITEM* pcRowsUndone,  
   HROW** prgRowsUndone,  
   DBROWSTATUS** prgRowStatus   
);  
```  
  
#### 參數  
 `hReserved`  
 \[對應至 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)的 `hChapter` 參數。  
  
 *pcRowsUndone*  
 \[對應至 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)的 `pcRows` 參數。  
  
 *prgRowsUndone*  
 \[對應至 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)的 *prgRows* 參數。  
  
 如需其他參數，請參閱《 *OLE DB 程式設計人員參考》的*[IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx) 。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)