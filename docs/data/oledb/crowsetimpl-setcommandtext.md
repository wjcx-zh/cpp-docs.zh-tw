---
title: "CRowsetImpl::SetCommandText | Microsoft Docs"
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
  - "CRowsetImpl.SetCommandText"
  - "CRowsetImpl::SetCommandText"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetCommandText 方法"
ms.assetid: e016d7df-c1a0-4dee-b19b-c876680221fd
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRowsetImpl::SetCommandText
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在兩個資料驗證和儲存 **DBID**的 \([m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) 和 [m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)\)。  
  
## 語法  
  
```  
  
      HRESULT CRowsetBaseImpl::SetCommandText(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### 參數  
 `pTableID`  
 \[out 代表資料表 ID. 的 **DBID** 的指標  
  
 `pIndexID`  
 \[out 代表索引 ID. 的 **DBID** 的指標  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 **SetCommentText** 方法由 `CreateRowset`， `IOpenRowsetImpl`樣板化靜態方法呼叫。  
  
 這個方法會呼叫 [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) 和 [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) 委派其工作將 upcasted 指標。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [CRowsetImpl 類別](../../data/oledb/crowsetimpl-class.md)