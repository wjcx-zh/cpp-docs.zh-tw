---
title: "istreambuf_iterator 類別 | Microsoft Docs"
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
  - "istreambuf_iterator"
  - "std.istreambuf_iterator"
  - "std::istreambuf_iterator"
  - "streambuf/std::istreambuf_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istreambuf_iterator 類別"
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
caps.latest.revision: 19
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# istreambuf_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別 istreambuf\_iterator 描述輸入迭代器物件，該物件從輸入資料流緩衝區擷取字元項目，並透過它所儲存的物件 \(屬於 `basic_streambuf`\<**CharType**, **Traits**\> 的 pointer 類型\) 存取項目。  
  
## 語法  
  
```  
  
      template <   
   class CharType  
   class Traits = char_traits<CharType>  
>  
class istreambuf_iterator  
: public iterator<input_iterator_tag, CharType, typename Traits::off_type, CharType *, CharType&>  
```  
  
#### 參數  
 `CharType`  
 類型，表示 istreambuf\_iterator 的字元類型。  
  
 `Traits`  
 類型，表示 istreambuf\_iterator 的字元類型。  這個引數是選擇性的，而且預設值是 `char_traits`\<*CharType\>。*  
  
## 備註  
 istreambuf\_iterator 類別必須符合輸入迭代器的需求。  
  
 在建構或遞增具有非 null 儲存指標的 istreambuf\_iterator 類別物件之後，物件會有效嘗試從關聯的輸入資料流擷取和儲存 **CharType** 類型物件。  然而，擷取可能會延遲，直到物件實際上已取值或複製。  如果擷取失敗，物件是實際上會將儲存的指標取代為 null 指標，因而建立序列結尾指標。  
  
### 建構函式  
  
|||  
|-|-|  
|[istreambuf\_iterator](../Topic/istreambuf_iterator::istreambuf_iterator.md)|建構 `istreambuf_iterator`，初始化以從輸入資料流讀取字元。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/istreambuf_iterator::char_type.md)|類型，提供 `ostreambuf_iterator` 的字元類型。|  
|[int\_type](../Topic/istreambuf_iterator::int_type.md)|類型，提供 `istreambuf_iterator` 的整數類型。|  
|[istream\_type](../Topic/istreambuf_iterator::istream_type.md)|類型，提供 `istream_iterator` 的資料流類型。|  
|[streambuf\_type](../Topic/istreambuf_iterator::streambuf_type.md)|類型，提供 `istreambuf_iterator` 的資料流類型。|  
|[traits\_type](../Topic/istream_iterator::traits_type.md)|類型，提供 `istream_iterator` 的字元特性類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[equal](../Topic/istreambuf_iterator::equal.md)|測試兩個輸入資料流緩衝區迭代器是否相等。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\*](../Topic/istreambuf_iterator::operator*.md)|取值運算子傳回資料流的下一個字元。|  
|[operator\+\+](../Topic/istreambuf_iterator::operator++.md)|從輸入資料流傳回下一個字元，或在遞增之前複製物件並傳回複本。|  
|[operator\-\>](../Topic/istreambuf_iterator::operator-%3E.md)|傳回成員的值 \(如果有\)。|  
  
## 需求  
 **標頭：**\<iterator\>  
  
 **命名空間:** std  
  
## 請參閱  
 [iterator 結構](../standard-library/iterator-struct.md)   
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)