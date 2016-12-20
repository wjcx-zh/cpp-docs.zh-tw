---
title: "CBulkRowset::MoveNext | Microsoft Docs"
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
  - "ATL.CBulkRowset<TAccessor>.MoveNext"
  - "ATL::CBulkRowset::MoveNext"
  - "CBulkRowset::MoveNext"
  - "ATL.CBulkRowset.MoveNext"
  - "CBulkRowset.MoveNext"
  - "ATL::CBulkRowset<TAccessor>::MoveNext"
  - "CBulkRowset<TAccessor>.MoveNext"
  - "CBulkRowset<TAccessor>::MoveNext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveNext 方法"
ms.assetid: 788f3344-cf60-4af1-8f5f-0098c8d1a3f0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBulkRowset::MoveNext
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取資料的下一行。  
  
## 語法  
  
```  
  
HRESULT MoveNext( ) throw( );  
  
```  
  
## 傳回值  
 標準版 `HRESULT` 當資料列集的結尾已經到達時，傳回 **DB\_S\_ENDOFROWSET**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CBulkRowset 類別](../../data/oledb/cbulkrowset-class.md)