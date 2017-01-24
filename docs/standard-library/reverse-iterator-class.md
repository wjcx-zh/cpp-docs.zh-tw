---
title: "reverse_iterator 類別 | Microsoft Docs"
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
  - "reverse_iterator"
  - "std::reverse_iterator"
  - "std.reverse_iterator"
  - "xutility/std::reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse_iterator 類別"
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
caps.latest.revision: 21
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# reverse_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此樣板類別是迭代器配接器，描述行為類似隨機存取或雙向迭代器，只不過是反向方向的反向迭代器物件。  它啟用範圍的向後周遊。  
  
## 語法  
  
```  
template <class RandomIterator>  
class reverse_iterator  
```  
  
#### 參數  
 RandomIterator  
 類型，表示要調整為反向操作的迭代器。  
  
## 備註  
 現有的標準範本庫容器也會定義 `reverse_iterator` 和 `const_reverse_iterator` 類型，並且具有可傳回反向迭代器的成員函式 `rbegin` 和 `rend`。  這些迭代器有覆寫語意。  `reverse_iterator` 配接器提供插入語意補充這項功能，也可以用於資料流。  
  
 需要雙向迭代器的 `reverse_iterator` 不可呼叫任何成員函式 `operator+=`、`operator+`、`operator-=`、`operator-` 或 `operator[]`，這些只能用於隨機存取迭代器。  
  
 如果迭代器的範圍是 \[`_First`, \_Last\)，其中左方括號表示 \_*First* 時包含，而右括號表示包含項目直到 \_*Left*，但不含 \_*Left* 本身。  相同項目包含在反向序列中 \[**rev** – `_First`, **rev** – \_*Left*\)，因此，如果 \_*Left* 是在序列中的超出結尾後一個 \(one\-past\-the\-end\) 項目，則反向序列中的第一個項目 **rev** – \_*First* 會指向 \*\(\_*Left* – 1 \)。  將所有反向迭代器與其基礎迭代器關聯的識別為：  
  
 &\*\(**reverse\_iterator** \( *i* \) \) \=\= &\*\( *i* – 1 \).  
  
 實際上，這表示在反向序列中 reverse\_iterator 會參考迭代器在原始序列中所參考項目之外 \(右側\) 一個位置的項目。  因此，如果迭代器定址序列 \(2, 4, 6, 8\) 中的項目 6，則 `reverse_iterator` 會定址反向序列 \(8, 6, 4, 2\) 中的項目 4。  
  
### 建構函式  
  
|||  
|-|-|  
|[reverse\_iterator](../Topic/reverse_iterator::reverse_iterator.md)|從基底迭代器建構預設的 `reverse_iterator` 或 `reverse_iterator`。|  
  
### Typedef  
  
|||  
|-|-|  
|[difference\_type](../Topic/reverse_iterator::difference_type.md)|類型，提供兩個參考同一容器內項目的 `reverse_iterator` 之間的差異。|  
|[iterator\_type](../Topic/reverse_iterator::iterator_type.md)|類型，提供 `reverse_iterator` 的基礎迭代器。|  
|[指標](../Topic/reverse_iterator::pointer.md)|類型，提供指向 `reverse_iterator` 定址的項目之指標。|  
|[reference](../Topic/reverse_iterator::reference.md)|類型，提供指向 `reverse_iterator` 定址的項目之參考。|  
  
### 成員函式  
  
|||  
|-|-|  
|[base](../Topic/reverse_iterator::base.md)|從其 `reverse_iterator` 復原基礎迭代器。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\*](../Topic/reverse_iterator::operator*.md)|傳回 `reverse_iterator` 定址的項目。|  
|[operator\+](../Topic/reverse_iterator::operator+.md)|將位移新增至迭代器，並傳回新的 `reverse_iterator`，定址在新的位移位置中插入的項目。|  
|[operator\+\+](../Topic/reverse_iterator::operator++.md)|遞增 `reverse_iterator` 至下一個項目。|  
|[operator\+\=](../Topic/reverse_iterator::operator+=.md)|加入 `reverse_iterator` 的指定位移。|  
|[operator\-](../Topic/reverse_iterator::operator-.md)|從 `reverse_iterator` 減去位移並傳回 `reverse_iterator`，定址在位移位置上的項目。|  
|[operator\-\-](../Topic/reverse_iterator::operator--.md)|遞減 `reverse_iterator` 至上一個項目。|  
|[operator\-\=](../Topic/reverse_iterator::operator-=.md)|從 `reverse_iterator` 減去指定位移。|  
|[operator\-\>](../Topic/reverse_iterator::operator-%3E.md)|傳回由 `reverse_iterator` 定址的項目之指標。|  
|[operator&#91;&#93;](../Topic/reverse_iterator::operator.md)|以指定的位置數目，從 `reverse_iterator` 定址的項目傳回項目位移的參考。|  
  
## 需求  
 **標頭：**\<iterator\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)