---
title: "ostream_iterator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ostream_iterator"
  - "std.ostream_iterator"
  - "std::ostream_iterator"
  - "iterator/std::ostream_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostream_iterator 類別"
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# ostream_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別 ostream\_iterator 描述輸出迭代器物件，這個物件使用擷取 **operator \<\<** 在輸出資料流中寫入後續項目。  
  
## 語法  
  
```  
  
      template <  
   class Type   
   class CharType = char  
   class Traits = char_traits<CharType>  
>  
class ostream_iterator  
```  
  
#### 參數  
 *Type*  
 要插入至輸出資料流的物件類型。  
  
 `CharType`  
 類型，表示 `ostream_iterator` 的字元類型。  這個引數是選擇性的，而且預設值是 `char`*。*  
  
 `Traits`  
 類型，表示 `ostream_iterator` 的字元類型。  這個引數是選擇性的，而且預設值是 `char_traits`\<*CharType\>。*  
  
 ostream\_iterator 類別必須符合輸出迭代器的需求。  使用 `ostream_iterator`，演算法可以直接寫入輸出資料流。  
  
### 建構函式  
  
|||  
|-|-|  
|[ostream\_iterator](../Topic/ostream_iterator::ostream_iterator.md)|建構初始化和分隔以寫入輸出資料流的 `ostream_iterator`。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/ostream_iterator::char_type.md)|類型，提供 `ostream_iterator` 的字元類型。|  
|[ostream\_type](../Topic/ostream_iterator::ostream_type.md)|類型，提供 `ostream_iterator` 的資料流類型。|  
|[traits\_type](../Topic/ostream_iterator::traits_type.md)|類型，提供 `ostream_iterator` 的字元特性類型。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\*](../Topic/ostream_iterator::operator*.md)|取值運算子，用來實作輸出迭代器運算式 \*`i` \= `x`。|  
|[operator\+\+](../Topic/ostream_iterator::operator++.md)|無作用的遞增運算子，傳回 `ostream_iterator`，指向在呼叫作業之前它所定址的相同物件。|  
|[operator\=](../Topic/ostream_iterator::operator=.md)|指派運算子，用來實作輸出迭代器運算式 \*`i` \= `x`，以寫入輸出資料流。|  
  
## 需求  
 **標頭：**\<iterator\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)