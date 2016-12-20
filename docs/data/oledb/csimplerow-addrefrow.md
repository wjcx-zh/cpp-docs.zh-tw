---
title: "CSimpleRow::AddRefRow | Microsoft Docs"
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
  - "CSimpleRow::AddRefRow"
  - "AddRefRow"
  - "ATL.CSimpleRow.AddRefRow"
  - "ATL::CSimpleRow::AddRefRow"
  - "CSimpleRow.AddRefRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRefRow 方法"
ms.assetid: 9bb5b7a5-79f2-4de5-852c-e9918fe67665
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleRow::AddRefRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將參考次數 \(Reference Count\) 加入至現有的資料列控制代碼以安全執行緒方式。  
  
## 語法  
  
```  
  
DWORD AddRefRow( );  
  
```  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [CSimpleRow 類別](../../data/oledb/csimplerow-class.md)   
 [CSimpleRow::ReleaseRow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)