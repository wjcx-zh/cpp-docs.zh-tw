---
title: "InterfaceTraits::FillArrayWithIid 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FillArrayWithIid 方法"
ms.assetid: 73583177-adc9-4fcb-917d-fa7e6d07c990
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# InterfaceTraits::FillArrayWithIid 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
__forceinline static void FillArrayWithIid(  
   _Inout_ unsigned long &index,  
   _In_ IID* iids  
);  
  
```  
  
#### 參數  
 `index`  
 含有一個以零起始的索引值之欄位的指標。  
  
 `iids`  
 介面 ID 的陣列。  
  
## 備註  
 指派 `Base` 介面 ID 至索引引數所指定的陣列元素。  
  
 與此 API 的名稱相反，只有一個陣列元素被修改；而不是整個陣列。  
  
 如需 `Base`的詳細資訊，請參閱 [InterfaceTraits 結構](../windows/interfacetraits-structure.md)的公用 Typedefs 部分。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [InterfaceTraits 結構](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)