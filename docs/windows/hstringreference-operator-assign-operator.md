---
title: "HStringReference::Operator= 運算子 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator="
dev_langs: 
  - "C++"
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HStringReference::Operator= 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將另一個 HStringReference 物件中的值移動至目前 HStringReference 物件。  
  
## 語法  
  
```cpp  
HStringReference& operator=(HStringReference&& other) throw()  
```  
  
#### 參數  
 `other`  
 現有的 HStringReference 物件。  
  
## 備註  
 現有的 `other` 物件的值複製到目前的 HString 物件，然後終結 `other` 物件。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HStringReference 類別](../windows/hstringreference-class.md)