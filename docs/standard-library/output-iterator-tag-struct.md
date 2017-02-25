---
title: "output_iterator_tag 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::output_iterator_tag"
  - "output_iterator_tag"
  - "xutility/std::output_iterator_tag"
  - "std.output_iterator_tag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "output_iterator_tag 類別"
  - "output_iterator_tag 結構"
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# output_iterator_tag 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別，為表示輸出迭代器的 **iterator\_category** 函式提供傳回類型。  
  
## 語法  
  
```  
  
struct output_iterator_tag {};  
  
```  
  
## 備註  
 因為編譯演算法選取的標記使用這些類別標記類別。 樣板函式必須找到迭代器引數之最特定的類別，讓它可以在編譯時期使用最有效率的演算法。 每個迭代器類型的 `Iterator`, ，`iterator_traits`\<`Iterator`\>**:: iterator\_category** 必須定義為最特定的類別標籤描述迭代器的行為。  
  
 型別是相同 **迭代器**\<**Iter**\>**:: iterator\_category** 時 **Iter** 描述可以做為輸出迭代器的物件。  
  
 此標籤上未參數化 `value_type` 或 `difference_type` 迭代器，就如同其他的迭代器標籤，因為輸出迭代器沒有 `value_type` 或 `difference_type`。  
  
## 範例  
 請參閱 [iterator\_traits](../standard-library/iterator-traits-struct.md) 或 [random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md) 如需如何使用 **iterator\_tag**s。  
  
## 需求  
 **標頭：**\<iterator\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)