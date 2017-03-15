---
title: "IsSame::value 常數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "internal/Microsoft::WRL::Details::IsSame::value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value 常數"
ms.assetid: ee72deff-54a2-4482-9967-49a86d07f834
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# IsSame::value 常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template <typename T1, typename T2>  
    struct IsSame  
    {  
        static const bool value = false;  
    };  
  
    template <typename T1>  
    struct IsSame<T1, T1>  
    {  
        static const bool value = true;  
    };  
  
```  
  
## 備註  
 表示型別是否與另一個型別相同。  
  
 `value` 是 **true** ，如果樣板參數相同， **false** ，如果樣板參數不同。  
  
## 需求  
 **標題:** internal.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [IsSame 結構](../windows/issame-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)