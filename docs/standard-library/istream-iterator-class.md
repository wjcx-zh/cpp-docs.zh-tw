---
title: "istream_iterator 類別 | Microsoft Docs"
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
  - "iterator/std::istream_iterator"
  - "std.istream_iterator"
  - "std::istream_iterator"
  - "istream_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istream_iterator 類別"
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
caps.latest.revision: 18
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# istream_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述輸入迭代器物件。  它從輸入資料流擷取 `Type` 類別的物件，並透過它所儲存的物件 \(屬於 `basic_istream`\<`CharType`, `Traits`\> 的 `pointer` 類型\) 存取。  
  
## 語法  
  
```  
template<class Type,  
    class CharType = char,  
    class Traits = char_traits<CharType>,  
    class Distance = ptrdiff_t,  
> class istream_iterator  
 : public iterator<  
        input_iterator_tag,  
        Type,   
        Distance,   
        const Type *,  
        const Type&  
    >;  
```  
  
#### 參數  
 `Type`  
 要輸入資料流擷取的物件類型。  
  
 `CharType`  
 類型，表示 `istream_iterator` 的字元類型。  這個引數是選擇性的，而且預設值是 `char`。  
  
 `Traits`  
 類型，表示 `istream_iterator` 的字元類型。  這個引數是選擇性的，而且預設值是 `char_traits`\<`CharType`\>。  
  
 `Distance`  
 帶正負號的整數類資料類型，表示 `istream_iterator` 的差異類型。  這個引數是選擇性的，而且預設值是 `ptrdiff_t`。  
  
 在建構或遞增具有非 null 儲存指標的 istream\_iterator 類別物件之後，物件會嘗試從關聯的輸入資料流擷取和儲存 `Type` 類型物件。  如果擷取失敗，物件是實際上會將儲存的指標取代為 null 指標，因而建立序列結尾指標。  
  
### 建構函式  
  
|||  
|-|-|  
|[istream\_iterator](../Topic/istream_iterator::istream_iterator.md)|建構資料流結尾迭代器做為預設 `istream_iterator`，或建構 `istream_iterator`，初始化為從中讀取的迭代器資料流類型。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/istream_iterator::char_type.md)|類型，提供 `istream_iterator` 的字元類型。|  
|[istream\_type](../Topic/istream_iterator::istream_type.md)|類型，提供 `istream_iterator` 的資料流類型。|  
|[traits\_type](../Topic/istream_iterator::traits_type.md)|類型，提供 `istream_iterator` 的字元特性類型。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\*](../Topic/istream_iterator::operator*.md)|取值運算子傳回 `Type` 類型 \(由 `istream_iterator` 定址\) 的儲存物件。|  
|[operator\-\>](../Topic/istream_iterator::operator-%3E.md)|傳回成員的值 \(如果有\)。|  
|[operator\+\+](../Topic/istream_iterator::operator++.md)|從輸入資料流擷取遞增物件，或在遞增之前複製物件並傳回複本。|  
  
## 需求  
 **標頭：**\<iterator\>  
  
 **命名空間:** std  
  
## 請參閱  
 [input\_iterator\_tag 結構](../standard-library/input-iterator-tag-struct.md)   
 [iterator 結構](../standard-library/iterator-struct.md)   
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)