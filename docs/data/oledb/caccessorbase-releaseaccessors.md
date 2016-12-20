---
title: "CAccessorBase::ReleaseAccessors | Microsoft Docs"
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
  - "CAccessorBase::ReleaseAccessors"
  - "CAccessorBase.ReleaseAccessors"
  - "ReleaseAccessors"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseAccessors 方法"
ms.assetid: f08bc88e-0552-4a9c-9c65-b4061094649a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccessorBase::ReleaseAccessors
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

釋放所建立的存取子。  
  
## 語法  
  
```  
  
      HRESULT ReleaseAccessors(  
   IUnknown* pUnk   
);  
```  
  
#### 參數  
 *浪費*  
 \[至 **IUnknown** 介面之指標的存取子建立 COM 物件的。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 呼叫 [CAccessorRowset::Close](../../data/oledb/caccessorrowset-close.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CAccessorBase 類別](../../data/oledb/caccessorbase-class.md)