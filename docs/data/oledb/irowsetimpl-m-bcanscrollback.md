---
title: "IRowsetImpl::m_bCanScrollBack | Microsoft Docs"
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
  - "IRowsetImpl::m_bCanScrollBack"
  - "ATL::IRowsetImpl::m_bCanScrollBack"
  - "IRowsetImpl.m_bCanScrollBack"
  - "ATL.IRowsetImpl.m_bCanScrollBack"
  - "m_bCanScrollBack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_bCanScrollBack"
ms.assetid: 69de3179-bf56-415e-935f-e98bcb34debe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetImpl::m_bCanScrollBack
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指出提供者是否可以將自己的游標反向移動。  
  
## 語法  
  
```  
  
unsigned  m_bCanScrollBack:1;  
  
```  
  
## 備註  
 與在 **DBPROPSET\_ROWSET** 群組中的 **DBPROP\_CANSCROLLBACKWARDS** 屬性連接。  提供者必須支援 **m\_bCanFetchBackwards** 的 **DBPROP\_CANSCROLLBACKWARDS** 能為 true。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m\_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)