---
title: "iterator 結構 | Microsoft Docs"
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
  - "iterator"
  - "std::iterator"
  - "std.iterator"
  - "xutility/std::iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator 類別"
  - "iterator 結構"
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# iterator 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用來建立空的基礎結構確保使用者自訂的 Iterator 類別適當地使用 **iterator\_trait**的 . 一起使用。  
  
## 語法  
  
```  
template<class Category, class Type, class Distance = ptrdiff_t  
    class Pointer = Type*, class Reference = Type&>  
    struct iterator {  
        typedef Category iterator_category;  
        typedef Type value_type;  
        typedef Distance difference_type;  
        typedef Distance distance_type;  
        typedef Pointer pointer;  
        typedef Reference reference;  
    };  
```  
  
## 備註  
 範本結構做為的基底型別 \(Base 所有 Iterator。  它定義成員型別  
  
-   `iterator_category` \(範本參數的 `Category`\) 的同義字。  
  
-   `value_type` \(範本參數的 \[**型別**\]\) 同義字。  
  
-   `difference_type` \(範本參數的 `Distance`\) 的同義字。  
  
-   `distance_type` \(範本參數的 `Distance`\) 同義資料表。  
  
-   `pointer` \(範本參數的 `Pointer`\) 的同義字。  
  
-   `reference` \(範本參數的 `Reference`\) 的同義字。  
  
 請注意 `value_type` 不應為常數型別，即使在常數 \[**型別**\] 和參考物件的 **pointer** 點選設定常數 \[**型別**\] 物件。  
  
## 範例  
 提供的範例參閱 [iterator\_traits](../standard-library/iterator-traits-struct.md) 宣告和使用型別在 Iterator 基底類別。  
  
## 需求  
 **Header:** \<Iterator\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)