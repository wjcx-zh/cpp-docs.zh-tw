---
title: "_bstr_t::operator = | Microsoft Docs"
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
  - "_bstr_t::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= 運算子, 使用特定 Visual C++ 物件"
  - "operator =, bstr"
  - "operator=, bstr"
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::operator =
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將新值指派給現有的 `_bstr_t` 物件。  
  
## 語法  
  
```  
  
      _bstr_t& operator=(  
   const _bstr_t& s1   
) throw ( );  
_bstr_t& operator=(  
   const char* s2   
);  
_bstr_t& operator=(  
   const wchar_t* s3   
);  
_bstr_t& operator=(  
   const _variant_t& var   
);  
```  
  
#### 參數  
 *s1*  
 `_bstr_t` 物件，將被指派給現有的 `_bstr_t` 物件。  
  
 *s2*  
 多位元組字串，將被指派給現有的 `_bstr_t` 物件。  
  
 `s3`  
 Unicode 字串，將被指派給現有的 `_bstr_t` 物件。  
  
 `var`  
 `_variant_t` 物件，將被指派給現有的 `_bstr_t` 物件。  
  
 **END Microsoft 特定的**  
  
## 範例  
 如需使用 `operator=` 的範例，請參閱 [\_bstr\_t::Assign](../cpp/bstr-t-assign.md)。  
  
## 請參閱  
 [\_bstr\_t 類別](../cpp/bstr-t-class.md)