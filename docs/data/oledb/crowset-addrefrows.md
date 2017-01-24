---
title: "CRowset::AddRefRows | Microsoft Docs"
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
  - "CRowset<TAccessor>.AddRefRows"
  - "CRowset.AddRefRows"
  - "ATL.CRowset.AddRefRows"
  - "AddRefRows"
  - "CRowset::AddRefRows"
  - "CRowset<TAccessor>::AddRefRows"
  - "ATL::CRowset::AddRefRows"
  - "ATL.CRowset<TAccessor>.AddRefRows"
  - "ATL::CRowset<TAccessor>::AddRefRows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRefRows 方法"
ms.assetid: 590b5a24-870f-4c42-b0c8-28491f368a82
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowset::AddRefRows
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) 來增加\(一\)與目前資料列控制代碼相關聯的參考計數。  
  
## 語法  
  
```  
  
HRESULT AddRefRows( ) throw( );  
  
```  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 這個方法會增加目前資料列控制代碼的參考計數。  呼叫 [ReleaseRows](../../data/oledb/crowset-releaserows.md) 減少計數。  以移動方法傳回之資料列有參考計數為一。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [CRowset::ReleaseRows](../../data/oledb/crowset-releaserows.md)