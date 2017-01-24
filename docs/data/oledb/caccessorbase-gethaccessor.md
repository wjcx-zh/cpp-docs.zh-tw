---
title: "CAccessorBase::GetHAccessor | Microsoft Docs"
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
  - "GetHAccessor"
  - "CAccessorBase::GetHAccessor"
  - "CAccessorBase.GetHAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetHAccessor 方法"
ms.assetid: 1bb98762-0752-4aae-a0b6-ba96bec03621
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorBase::GetHAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取指定之存取子的存取子控制代碼。  
  
## 語法  
  
```  
  
      HACCESSOR GetHAccessor(  
   ULONG nAccessor   
) const;  
```  
  
#### 參數  
 `nAccessor`  
 \[in\] 存取子的零的數字。  
  
## 傳回值  
 存取子的控制代碼。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CAccessorBase 類別](../../data/oledb/caccessorbase-class.md)