---
title: "char_traits&lt;wchar_t&gt; 結構 | Microsoft Docs"
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
  - "std.char_traits<wchar_t>"
  - "char_traits<wchar_t>"
  - "string/std::char_traits<wchar_t>"
  - "std::char_traits<wchar_t>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits<wchar_t> 類別"
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# char_traits&lt;wchar_t&gt; 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為範本結構 **char\_traits\<CharType\>** 特製化的 `wchar_t`型別元素的類別。  
  
## 語法  
  
```  
template<> struct char_traits<wchar_t>;  
```  
  
## 備註  
 特製化允許結構利用操作 `wchar_t`型別物件的程式庫函式。  
  
## 需求  
 **標頭：**\<string\>  
  
 **命名空間:** std  
  
## 請參閱  
 [char\_traits 結構](../standard-library/char-traits-struct.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)