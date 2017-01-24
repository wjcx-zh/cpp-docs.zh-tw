---
title: "_variant_t 關係運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t::operator=="
  - "_variant_t.operator!="
  - "_variant_t::operator!="
  - "_variant_t.operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= 運算子"
  - "== 運算子, 使用特定 Visual C++ 物件"
  - "運算子 !=, 關係運算子"
  - "運算子 !=, variant"
  - "運算子 ==, variant"
  - "operator!=, 關係運算子"
  - "operator!=, variant"
  - "operator==, variant"
  - "關係運算子, _variant_t 類別"
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t 關係運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 比較兩個 `_variant_t` 物件是否相等或不等。  
  
## 語法  
  
```  
  
      bool operator==(  
   const VARIANT& varSrc   
) const;  
bool operator==(  
   const VARIANT* pSrc   
) const;  
bool operator!=(  
   const VARIANT& varSrc   
) const;  
bool operator!=(  
   const VARIANT* pSrc   
) const;  
```  
  
#### 參數  
 *varSrc*  
 要與 `_variant_t` 比較的 **VARIANT**。  
  
 `pSrc`  
 要與 `_variant_t` 比較的 **VARIANT** 指標。  
  
## 傳回值  
 如果對等成立則傳回 **true**，否則便傳回 **false**。  
  
## 備註  
 將 `_variant_t` 物件與 **VARIANT** 比較，測試是否相等或不等。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_variant\_t 類別](../cpp/variant-t-class.md)