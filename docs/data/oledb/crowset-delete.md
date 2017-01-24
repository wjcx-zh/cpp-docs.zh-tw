---
title: "CRowset::Delete | Microsoft Docs"
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
  - "ATL::CRowset::Delete"
  - "CRowset.Delete"
  - "CRowset::Delete"
  - "ATL.CRowset.Delete"
  - "ATL::CRowset<TAccessor>::Delete"
  - "CRowset<TAccessor>.Delete"
  - "CRowset<TAccessor>::Delete"
  - "ATL.CRowset<TAccessor>.Delete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Delete 方法"
ms.assetid: 4feb4f7e-139f-489a-b7d5-ea6ec0058e0f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::Delete
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 [IRowsetChange::DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx) 從資料列集刪除目前的資料列。  
  
## 語法  
  
```  
  
HRESULT Delete( ) const throw( );  
  
```  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)