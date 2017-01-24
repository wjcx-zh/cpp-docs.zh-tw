---
title: "ICommandImpl::m_bIsExecuting | Microsoft Docs"
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
  - "ICommandImpl.m_bIsExecuting"
  - "ATL::ICommandImpl::m_bIsExecuting"
  - "m_bIsExecuting"
  - "ATL.ICommandImpl.m_bIsExecuting"
  - "ICommandImpl::m_bIsExecuting"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_bIsExecuting"
ms.assetid: 1e152164-514c-4116-88a3-16984af99991
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandImpl::m_bIsExecuting
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示命令目前是否為不可執行狀態。  
  
## 語法  
  
```  
  
unsigned m_bIsExecuting:1;  
  
```  
  
## 備註  
 您的命令類別 **Execute** 方法可以設定這個變數至 **true**。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [ICommandImpl 類別](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m\_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)