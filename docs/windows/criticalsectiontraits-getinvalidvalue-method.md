---
title: "CriticalSectionTraits::GetInvalidValue 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInvalidValue 方法"
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSectionTraits::GetInvalidValue 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

特製化 CriticalSection 範本，讓範本永遠無效。  
  
## 語法  
  
```  
inline static Type GetInvalidValue();  
```  
  
## 傳回值  
 永遠傳回指向無效的關鍵區段的指標。  
  
## 備註  
 *Type* 修飾詞定義為 `typedef CRITICAL_SECTION* Type;`。  
  
## 需求  
 **標頭：**corewrappers.h  
  
 **命名空間:** Microsoft::WRL::Wrappers::HandleTraits  
  
## 請參閱  
 [CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)