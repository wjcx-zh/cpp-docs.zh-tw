---
title: "CompareStringOrdinal 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal"
dev_langs: 
  - "C++"
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# CompareStringOrdinal 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```cpp  
  
inline INT32 CompareStringOrdinal(  
   HSTRING lhs,   
   HSTRING rhs)  
```  
  
#### 參數  
 `lhs`  
 要比較的第一個 HSTRING 字串。  
  
 `rhs`  
 要比較的第二個 HSTRING 字串。  
  
## 傳回值  
  
|值|條件|  
|-------|--------|  
|\-1|`lhs` 小於 `rhs`。|  
|0|`lhs` 等於 `rhs`。|  
|1|`lhs` 大於 `rhs`。|  
  
## 備註  
 比較兩個指定的 HSTRING 物件，並傳回一個整數，指出它們在排序順序中的相對位置。  
  
## 需求  
 **標頭：**corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## 請參閱  
 [Microsoft::WRL::Wrappers::Details 命名空間](../windows/microsoft-wrl-wrappers-details-namespace.md)