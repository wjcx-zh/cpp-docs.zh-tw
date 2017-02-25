---
title: "raw_storage_iterator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::raw_storage_iterator"
  - "raw_storage_iterator"
  - "std.raw_storage_iterator"
  - "memory/std::raw_storage_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "raw_storage_iterator 類別"
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# raw_storage_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供的配接器類別，可讓演算法將其結果儲存至未初始化的記憶體。  
  
## 語法  
  
```  
  
        template <class   
        OutputIterator,  
         class   
        Type>  
class raw_storage_iterator  
```  
  
#### 參數  
 `OutputIterator`  
 指定要儲存之物件的輸出迭代器。  
  
 *類型*  
 正在配置儲存體的物件類型。  
  
## 備註  
 此類別描述輸出迭代器，該迭代器在它所產生的序列中建構 \[類型\] 類型的物件。  `raw_storage_iterator`\<**ForwardIterator**, **Type**\> 類別的物件會藉由類別為 **ForwardIterator** 的正向迭代器物件 \(建構物件時所指定的\) 存取儲存體。  針對 **ForwardIterator** 類別的第一個物件，運算式 **&\*first** 必須指定未建構的儲存體給此產生之序列的下一個物件 \(類型為 \[類型\]\)。  
  
 當有需要分隔記憶體配置和物件建構時，會使用此配接器類別。  `raw_storage_iterator` 可以用來將物件複製到未初始化的儲存體，例如使用`malloc` 函式配置的記憶體。  
  
## 成員  
  
### 建構函式  
  
|||  
|-|-|  
|[raw\_storage\_iterator](../Topic/raw_storage_iterator::raw_storage_iterator.md)|藉由指定的基礎輸出迭代器建構原始儲存體迭代器。|  
  
### Typedef  
  
|||  
|-|-|  
|[element\_type](../Topic/raw_storage_iterator::element_type.md)|提供一個類型，其描述要儲存在原始儲存體的項目。|  
|[iter\_type](../Topic/raw_storage_iterator::iter_type.md)|提供一個類型，其描述為原始儲存體迭代器基礎的迭代器。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\*](../Topic/raw_storage_iterator::operator*.md)|取值運算子，用來實作輸出迭代器運算式 \*`ii` \= `x`。|  
|[operator\=](../Topic/raw_storage_iterator::operator=.md)|指派運算子，用來實作原始儲存體迭代器運算式 \*`i` \= `x` 以儲存於記憶體中。|  
|[operator\+\+](../Topic/raw_storage_iterator::operator++.md)|原始儲存體迭代器的前置遞增和後置遞增運算子。|  
  
## 需求  
 **標頭：**\<memory\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)