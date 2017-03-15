---
title: "HStringReference::Operator== 運算子 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=="
dev_langs: 
  - "C++"
ms.assetid: cad3d52d-cd67-4194-a270-5239b1121a09
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HStringReference::Operator== 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示兩個參數是否相等。  
  
## 語法  
  
```cpp  
  
inline bool operator==(  
               const HStringReference& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HSTRING& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HStringReference& lhs,   
               const HSTRING& rhs) throw()  
  
```  
  
#### 參數  
 `lhs`  
 要比較的第一個參數。  `lhs` 可以是 HStringReference 物件或 HSTRING 控制代碼。  
  
 `rhs`  
 要比較的第二個參數。`rhs` 可以是 HStringReference 物件或 HSTRING 控制代碼。  
  
## 傳回值  
 如果 `lhs` 和 `rhs` 參數相等，則為 `true`，否則為 `false`。  
  
## 需求  
 **標頭：**corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HStringReference 類別](../windows/hstringreference-class.md)