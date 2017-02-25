---
title: "ostreambuf_iterator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.ostreambuf_iterator"
  - "streambuf/std::ostreambuf_iterator"
  - "ostreambuf_iterator"
  - "std::ostreambuf_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostreambuf_iterator 類別"
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# ostreambuf_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別 ostreambuf\_iterator 描述輸出迭代器物件，這個物件使用擷取 **operator\>\>** 在輸出資料流中寫入後續字元項目。  `ostreambuf_iterator` 不同於 [ostream\_iterator 類別](../standard-library/ostream-iterator-class.md)，因為是字元 \(而非泛型類型\) 做為要插入至輸出資料流的物件類型。  
  
## 語法  
  
```  
  
      template <   
   class CharType = char  
   class Traits = char_traits<CharType>  
>  
```  
  
#### 參數  
 `CharType`  
 類型，表示 ostreambuf\_iterator 的字元類型。  這個引數是選擇性的，而且預設值是 `char`*。*  
  
 `Traits`  
 類型，表示 ostreambuf\_iterator 的字元類型。  這個引數是選擇性的，而且預設值是 `char_traits`\<*CharType\>。*  
  
## 備註  
 ostreambuf\_iterator 類別必須符合輸出迭代器的需求。  使用 `ostreambuf_iterator`，演算法可以直接寫入輸出資料流。  此類別提供低階資料流迭代器，允許存取字元格式的原始 \(未格式化\) I\/O 資料流，也能夠略過與進階資料流迭代器相關聯的緩衝和字元轉譯。  
  
### 建構函式  
  
|||  
|-|-|  
|[ostreambuf\_iterator](../Topic/ostreambuf_iterator::ostreambuf_iterator.md)|建構 `ostreambuf_iterator`，初始化以將字元寫入輸出資料流中。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/ostreambuf_iterator::char_type.md)|類型，提供 `ostreambuf_iterator` 的字元類型。|  
|[ostream\_type](../Topic/ostreambuf_iterator::ostream_type.md)|類型，提供 `ostream_iterator` 的資料流類型。|  
|[streambuf\_type](../Topic/ostreambuf_iterator::streambuf_type.md)|類型，提供 `ostreambuf_iterator` 的資料流類型。|  
|[traits\_type](../Topic/ostreambuf_iterator::traits_type.md)|類型，提供 `ostream_iterator` 的字元特性類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[failed](../Topic/ostreambuf_iterator::failed.md)|測試插入至輸出資料流緩衝區是否失敗。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\*](../Topic/ostreambuf_iterator::operator*.md)|取值運算子，用來實作輸出迭代器運算式 \*`i` \= `x`。|  
|[operator\+\+](../Topic/ostreambuf_iterator::operator++.md)|無作用的遞增運算子，傳回 `ostreambuf_iterator`，指向在呼叫作業之前它所定址的相同物件。|  
|[operator\=](../Topic/ostreambuf_iterator::operator=.md)|此運算子會將字元插入至相關聯的資料流緩衝區。|  
  
## 需求  
 **標頭：**\<iterator\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)