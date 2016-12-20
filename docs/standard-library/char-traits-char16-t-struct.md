---
title: "char_traits&lt;char16_t&gt; 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::char_traits<char16_t>"
  - "std.char_traits<char16_t>"
  - "char_traits<char16_t>"
  - "string/std::char_traits<char16_t>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits<char16_t> 類別"
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# char_traits&lt;char16_t&gt; 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為範本結構 **char\_traits\<CharType\>** 特製化的 `char16_t`型別元素的結構。  
  
## 語法  
  
```  
template<> struct char_traits<char16_t>;  
```  
  
## 備註  
 特製化允許結構利用操作這個型別 `char16_t`之物件的程式庫函式。  
  
## 需求  
 **標頭：**\<string\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<string\>](../standard-library/string.md)   
 [char\_traits 結構](../standard-library/char-traits-struct.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)