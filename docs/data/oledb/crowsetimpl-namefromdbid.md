---
title: "CRowsetImpl::NameFromDBID | Microsoft Docs"
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
  - "CRowsetImpl.NameFromDBID"
  - "CRowsetImpl::NameFromDBID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NameFromDBID 方法"
ms.assetid: 6aa5b074-90c7-4434-adfd-c64c13e76c78
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::NameFromDBID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 **DBID** 擷取字串複製並傳遞至 `bstr` 。  
  
## 語法  
  
```  
  
      HRESULT CRowsetBaseImpl::NameFromDBID(  
   DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex   
);  
```  
  
#### 參數  
 *pDBID*  
 \[in\] 擷取 **DBID** 字串的指標。  
  
 `bstr`  
 \[in\] [CComBSTR](../../atl/reference/ccombstr-class.md) 參考以放置 **DBID** 字串的副本。  
  
 `bIndex`  
 \[in\] 如果索引 **DBID** 則是 **true** ； 如果 **DBID** 資料表則為 **false** 。  
  
## 傳回值  
 標準版 `HRESULT` 視 **DBID** 是否為資料表或索引 \(以 `bIndex`表示\)，則方法會傳回 **DB\_E\_NOINDEX** 或 **DB\_E\_NOTABLE**。  
  
## 備註  
 這個方法是由 [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) 和 [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)的 `CRowsetImpl` 實作所呼叫。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [CRowsetImpl 類別](../../data/oledb/crowsetimpl-class.md)