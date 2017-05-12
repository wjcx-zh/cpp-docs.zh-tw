---
title: "Platform::Collections::BackInsertIterator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator 類別"
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::Collections::BackInsertIterator 類別
代表將元素插入 \(而不是覆寫\) 序列集合後端的迭代器。  
  
## 語法  
  
```  
template <  
   typename T  
>  
class BackInsertIterator : public ::std::iterator< ::std::output_iterator_tag, void, void, void, void>;  
```  
  
#### 參數  
 `T`  
 目前集合中的項目類型。  
  
## 備註  
 BackInsertIterator 類別實作 [back\_insert\_iterator 類別](../standard-library/back-insert-iterator-class.md) 所需的規則。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[BackInsertIterator::BackInsertIterator 建構函式](../cppcx/backinsertiterator-backinsertiterator-constructor.md)|初始化 BackInsertIterator 類別的新執行個體。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[BackInsertIterator::operator\* 運算子](../cppcx/backinsertiterator-operator-dereference-operator.md)|擷取目前 BackInsertIterator 的參考。|  
|[BackInsertIterator::operator\+\+ 運算子](../cppcx/backinsertiterator-operator-increment-operator.md)|傳回目前 BackInsertIterator 的參考。 迭代器是未修改的。|  
|[BackInsertIterator::operator\= 運算子](../cppcx/backinsertiterator-operator-assign-operator.md)|將指定的物件附加至目前循序集合的結尾。|  
  
## 繼承階層  
 `BackInsertIterator`  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)