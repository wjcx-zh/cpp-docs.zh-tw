---
title: "HString::Operator== 運算子 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString::operator=="
dev_langs: 
  - "C++"
ms.assetid: 77ff4c1a-e62a-4256-bf9d-0f017137c630
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::Operator== 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示兩個參數是否相等。  
  
## 語法  
  
```cpp  
  
inline bool operator==(  
               const HString& lhs,   
               const HString& rhs) throw()  
  
inline bool operator==(  
                const HString& lhs,   
                const HStringReference& rhs) throw()  
  
inline bool operator==(  
                const HStringReference& lhs,   
                const HString& rhs) throw()  
  
inline bool operator==(  
                 const HSTRING& lhs,   
                 const HString& rhs) throw()  
  
inline bool operator==(  
                 const HString& lhs,   
                 const HSTRING& rhs) throw()  
  
```  
  
#### 參數  
 `lhs`  
 要比較的第一個參數。  `lhs` 可以是 HString 或 HStringReference 物件或 HSTRING 控制代碼。  
  
 `rhs`  
 要比較的第二個參數。`rhs` 可以是 HString 或 HStringReference 物件或 HSTRING 控制代碼。  
  
## 傳回值  
 如果 `lhs` 和 `rhs` 參數相等，則為 `true`，否則為 `false`。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HString 類別](../windows/hstring-class.md)