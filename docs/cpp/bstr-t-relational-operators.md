---
title: "_bstr_t 關係運算子 | Microsoft Docs"
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
  - "_bstr_t::operator>"
  - "_bstr_t::operator=="
  - "_bstr_t::operator>="
  - "_bstr_t::operator!="
  - "_bstr_t::operator<"
  - "_bstr_t::operator<="
  - "_bstr_t::operator!"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= 運算子"
  - "< 運算子, 比較特定物件"
  - "<= 運算子, 使用特定物件"
  - "== 運算子, 使用特定 Visual C++ 物件"
  - "> 運算子, 比較特定物件"
  - ">= 運算子, 比較特定物件"
  - "運算子 !=, 關係運算子"
  - "運算子 <, bstr"
  - "運算子 <=, bstr"
  - "運算子 ==, bstr"
  - "運算子 >, bstr"
  - "運算子 >=, bstr"
  - "operator!=, 關係運算子"
  - "operator<, bstr"
  - "operator<=, bstr"
  - "operator==, bstr"
  - "operator>=, bstr"
  - "關係運算子, _bstr_t 類別"
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t 關係運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 比較兩個 `_bstr_t` 物件。  
  
## 語法  
  
```  
  
      bool operator!( ) const throw( );   
bool operator==(  
   const _bstr_t& str   
) const throw( );  
bool operator!=(  
   const _bstr_t& str   
) const throw( );  
bool operator<(  
   const _bstr_t& str   
) const throw( );  
bool operator>(  
   const _bstr_t& str   
) const throw( );  
bool operator<=(  
   const _bstr_t& str   
) const throw( );  
bool operator>=(  
   const _bstr_t& str   
) const throw( );  
```  
  
## 備註  
 這些運算子會針對兩個 `_bstr_t` 物件進行字彙上的比較。  如果比較有效，運算子會傳回 **true**，否則會傳回 **false**。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_bstr\_t 類別](../cpp/bstr-t-class.md)