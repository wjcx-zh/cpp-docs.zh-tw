---
title: "IRowsetImpl::m_bReset | Microsoft Docs"
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
  - "ATL.IRowsetImpl.m_bReset"
  - "IRowsetImpl.m_bReset"
  - "m_bReset"
  - "IRowsetImpl::m_bReset"
  - "ATL::IRowsetImpl::m_bReset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_bReset"
ms.assetid: d423f9f3-4d48-4d0c-b152-684c81a0b34e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::m_bReset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用於的位元旗標決定游標位置是否定義資料列集的。  
  
## 語法  
  
```  
  
unsigned m_bReset:1;  
  
```  
  
## 備註  
 如果消費者呼叫 [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) 和負 `lOffset` 或 *烏鴉* 和 `m_bReset` 為 true 時，將 `GetNextRows` 移至資料列集的結尾。  如果 `m_bReset` 為 false，消費者符合 OLE DB 規格收到錯誤碼，。  `m_bReset` 旗標集合 **true** ，當資料列集初次建立時，而且，當消費者呼叫 [IRowsetImpl::RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)時。  在呼叫 `GetNextRows`時，會有集合 **false** 。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)