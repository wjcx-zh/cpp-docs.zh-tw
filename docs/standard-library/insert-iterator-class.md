---
title: "insert_iterator 類別 | Microsoft Docs"
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
  - "std::insert_iterator"
  - "iterator/std::insert_iterator"
  - "std.insert_iterator"
  - "insert_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert_iterator 類別"
  - "insert_iterator 類別, 語法"
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
caps.latest.revision: 17
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# insert_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述滿足輸出迭代器需求的迭代器配接器。  它在序列中插入項目 \(而不是覆寫\)，因此其語意不同於 C\+\+ 序列容器和關聯容器的迭代器所提供的覆寫語意。  `insert_iterator` 類別是根據所調整容器的類型樣板化。  
  
## 語法  
  
```  
template <class Container> class insert_iterator;  
```  
  
#### 參數  
 `Container`  
 容器的類型，`insert_iterator` 將在其中插入項目。  
  
## 備註  
 **Container** 類型容器必須滿足可變大小容器的需求，而且具有兩個引數的插入成員函式，其中參數的類型為 **Container::iterator** 和 **Container::value\_type**，並傳回 **Container::iterator** 類型。  標準範本庫序列容器和已排序關聯容器滿足這些需求，且可以調整以搭配 `insert_iterator` 使用。  對於關聯容器，位置引數視為提示，可能會根據提示品質改善或降低效能。  `insert_iterator` 一定要以其容器初始化。  
  
### 建構函式  
  
|||  
|-|-|  
|[insert\_iterator](../Topic/insert_iterator::insert_iterator.md)|建構 `insert_iterator`，將項目插入容器中的指定位置。|  
  
### Typedef  
  
|||  
|-|-|  
|[container\_type](../Topic/insert_iterator::container_type.md)|類型，表示要執行一般插入的容器。|  
|[reference](../Topic/insert_iterator::reference.md)|類型，提供關聯容器控制之序列中項目的參考。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\*](../Topic/insert_iterator::operator*.md)|取值運算子，用來實作輸出迭代器運算式 \*`i` \= `x` 以進行一般插入。|  
|[operator\+\+](../Topic/insert_iterator::operator++.md)|將 `insert_iterator` 遞增至可儲存值的下一個位置。|  
|[operator\=](../Topic/insert_iterator::operator=.md)|指派運算子，用來實作輸出迭代器運算式 \*`i` \= `x` 以進行一般插入。|  
  
## 需求  
 **標頭**：\<iterator\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)