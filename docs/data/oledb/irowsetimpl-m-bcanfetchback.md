---
title: "IRowsetImpl::m_bCanFetchBack | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetImpl.m_bCanFetchBack"
  - "ATL::IRowsetImpl::m_bCanFetchBack"
  - "IRowsetImpl.m_bCanFetchBack"
  - "IRowsetImpl::m_bCanFetchBack"
  - "m_bCanFetchBack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_bCanFetchBack"
ms.assetid: cfa007b0-7ba5-48a3-9d05-9f1916305fb7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::m_bCanFetchBack
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指出提供者是否支援向後擷取。  
  
## 語法  
  
```  
  
unsigned m_bCanFetchBack:1;  
  
```  
  
## 備註  
 與 **DBPROP\_CANFETCHBACKWARDS** 連接屬性在 **DBPROPSET\_ROWSET** 群組中。  提供者必須支援 **m\_bCanFetchBackwards** 的 **DBPROP\_CANFETCHBACKWARDS** 能為 true。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m\_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)