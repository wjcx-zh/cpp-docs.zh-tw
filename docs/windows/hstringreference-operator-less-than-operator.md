---
title: "HStringReference::Operator&lt; 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<"
dev_langs: 
  - "C++"
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HStringReference::Operator&lt; 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示第一個參數是否小於第二個參數。  
  
## 語法  
  
```cpp  
  
inline bool operator<(  
    const HStringReference& lhs,   
    const HStringReference& rhs) throw()  
  
```  
  
#### 參數  
 `lhs`  
 要比較的第一個參數。  `lhs` 可能為對 HStringReference 的參考。  
  
 `rhs`  
 要比較的第二個參數。 `rhs` 可以是 HStringReference 的參考。  
  
## 傳回值  
 `true` ，如果 `lhs` 參數小於 `rhs` 參數;否則， `false`。  
  
## 需求  
 **標頭：**corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HStringReference 類別](../windows/hstringreference-class.md)