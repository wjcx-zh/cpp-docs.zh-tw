---
title: "input_iterator_tag 結構 | Microsoft Docs"
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
  - "input_iterator_tag"
  - "std.input_iterator_tag"
  - "std::input_iterator_tag"
  - "xutility/std::input_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "input_iterator_tag 類別"
  - "input_iterator_tag 結構"
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# input_iterator_tag 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**iterator\_category** 為函式的傳回型別代表輸入 Iterator 的類別。  
  
## 語法  
  
```  
  
struct input_iterator_tag {};  
  
```  
  
## 備註  
 類別將類別標記為演算法選取使用編譯標記。  樣板函式需要尋找其 Iterator 引數最特定的類別，以便使用最有效的演算法在編譯時期。  對於型別 `Iterator`Iterator，必須定義 `iterator_traits`\<`Iterator`\>**::iterator\_category** 是描述 Iterator 的行為的最特定的分類標記。  
  
 這個型別與 **iterator**\<**Iter**\>**::iterator\_category** ，當 **Iter** 描述可做為輸入 Iterator 的物件時。  
  
## 範例  
 提供的範例參閱 [iterator\_traits](../standard-library/iterator-traits-struct.md) 或 [random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md) 使用 **iterator\_tag**的。  
  
## 需求  
 **標頭：**\<迭代器\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)