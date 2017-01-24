---
title: "HString::Operator= 運算子 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString::operator="
dev_langs: 
  - "C++"
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::Operator= 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將另一個 HString 物件中的值移至目前 HString 物件。  
  
## 語法  
  
```cpp  
HString& operator=(HString&& other) throw()  
```  
  
#### 參數  
 `other`  
 現有的 HString 物件。  
  
## 備註  
 現有的 `other` 物件的值複製到目前的 HString 物件，然後終結 `other` 物件。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HString 類別](../windows/hstring-class.md)