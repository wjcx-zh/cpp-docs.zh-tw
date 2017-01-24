---
title: "IRowsetImpl::SetDBStatus | Microsoft Docs"
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
  - "IRowsetImpl.SetDBStatus"
  - "IRowsetImpl::SetDBStatus"
  - "SetDBStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetDBStatus 方法"
ms.assetid: b73f526a-4fc6-4adb-9611-c3cca2cddb23
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::SetDBStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定指定之欄位的 `DBSTATUS` 狀態旗標。  
  
## 語法  
  
```  
  
      virtual HRESULT SetDBStatus(  
   DBSTATUS* statusFlags,  
   RowClass* currentRow,  
   ATLCOLUMNINFO* columnInfo   
);  
```  
  
#### 參數  
 `statusFlags`  
 [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx) 旗標為資料行設定。  
  
 `currentRow`  
 目前的資料列。  
  
 *columnInfo*  
 狀態設為的資料行。  
  
## 傳回值  
 標準 `HRESULT` 值。  
  
## 備註  
 提供者會覆寫這個函式為 **DBSTATUS\_S\_ISNULL** 和 **DBSTATUS\_S\_DEFAULT**提供特殊處理。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)