---
title: "HString::Attach 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString::Attach"
dev_langs: 
  - "C++"
ms.assetid: 69451979-0014-4959-bc5c-1e4ab6fb28e4
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::Attach 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

會將指定的 HString 物件與目前的 HString 物件關聯。  
  
## 語法  
  
```  
  
void Attach(  
       HSTRING hstr  
       ) throw()  
```  
  
#### 參數  
 `hstr`  
 現有的 HString 物件。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HString 類別](../windows/hstring-class.md)