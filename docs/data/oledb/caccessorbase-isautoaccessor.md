---
title: "CAccessorBase::IsAutoAccessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IsAutoAccessor"
  - "CAccessorBase.IsAutoAccessor"
  - "CAccessorBase::IsAutoAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsAutoAccessor 方法"
ms.assetid: c330da15-2947-4050-ad00-8f776adc58fb
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CAccessorBase::IsAutoAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果資料為存取子自動擷取在移動作業期間，則傳回 true。  
  
## 語法  
  
```  
  
      bool IsAutoAccessor(  
   ULONG nAccessor   
) const;  
```  
  
#### 參數  
 `nAccessor`  
 \[存取子的零的數字。  
  
## 傳回值  
 如果存取子是 autoaccessor，傳回 **true** 。  否則，它會傳回 **false**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CAccessorBase 類別](../../data/oledb/caccessorbase-class.md)