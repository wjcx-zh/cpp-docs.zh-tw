---
title: "IRowsetImpl::GetDBStatus | Microsoft Docs"
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
  - "GetDBStatus"
  - "IRowsetImpl.GetDBStatus"
  - "IRowsetImpl::GetDBStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetDBStatus 方法"
ms.assetid: e51d8ee2-fc0c-4909-861c-026c94fb0dfc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::GetDBStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回指定之欄位的 `DBSTATUS` 狀態旗標。  
  
## 語法  
  
```  
  
      virtual DBSTATUS GetDBStatus(  
   RowClass* currentRow,  
   ATLCOLUMNINFO* columnNames   
);  
```  
  
#### 參數  
 \[in\] `currentRow`  
 目前的資料列。  
  
 \[in\] `columnNames`  
 狀態所要求的資料列。  
  
## 傳回值  
 行的 [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) 旗標。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)