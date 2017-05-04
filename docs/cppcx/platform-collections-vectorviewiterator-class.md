---
title: "Platform::Collections::VectorViewIterator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator 類別"
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Collections::VectorViewIterator 類別
為衍生自 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]`IVectorView` 介面的物件提供標準樣板程式庫迭代器。  
  
 `ViewVectorIterator` 這個 Proxy 迭代器可以儲存類型為 `VectorProxy<T>` 的元素。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## 語法  
  
```  
template <  
   typename T  
>  
class VectorViewIterator;  
```  
  
#### 參數  
 `T`  
 VectorViewIterator 樣板類別的 typename。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`difference_type`|指標差異 \(ptrdiff\_t\)。|  
|`iterator_category`|隨機存取迭代器的分類 \(::std::random\_access\_iterator\_tag\)。|  
|`pointer`|VectorViewIterator 的實作所需的內部類型指標。|  
|`reference`|VectorViewIterator 的實作所需的內部類型參考。|  
|`value_type`|`T` typename。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[VectorViewIterator::VectorViewIterator 建構函式](../cppcx/vectorviewiterator-vectorviewiterator-constructor.md)|初始化 VectorViewIterator 類別的新執行個體。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[VectorViewIterator::operator\- 運算子](../cppcx/vectorviewiterator-operator-minus-operator.md)|從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。|  
|[VectorViewIterator::operator\-\- 運算子](../cppcx/vectorviewiterator-operator-decrement-operator.md)|遞減目前 VectorViewIterator。|  
|[VectorViewIterator::operator\!\= 運算子](../cppcx/vectorviewiterator-operator-inequality-operator.md)|指出目前 VectorViewIterator 是否不等於指定的 VectorViewIterator。|  
|[VectorViewIterator::operator\* 運算子](../cppcx/vectorviewiterator-operator-dereference-operator.md)|擷取目前 VectorViewIterator 指定的元素的參考。|  
|[VectorViewIterator::operatorOperator](../cppcx/vectorviewiterator-operatoroperator.md)|擷取從目前 VectorViewIterator 開始指定位移之項目的參考。|  
|[VectorViewIterator::operator\+ 運算子](../cppcx/vectorviewiterator-operator-plus-operator.md)|傳回 VectorViewIterator ，參考從指定的 VectorViewIterator 開始指定位移的項目。|  
|[VectorViewIterator::operator\+\+ 運算子](../cppcx/vectorviewiterator-operator-increment-operator.md)|遞增目前 VectorViewIterator。|  
|[VectorViewIterator::operator\+\= 運算子](../cppcx/vectorviewiterator-operator-plus-assign-operator.md)|依指定的位移遞增目前 VectorViewIterator。|  
|[VectorViewIterator::operator\< 運算子](../cppcx/vectorviewiterator-operator-less-than-operator.md)|指出目前 VectorViewIterator 是否小於指定的 VectorViewIterator。|  
|[VectorViewIterator::operator\<\= 運算子](../cppcx/vectorviewiterator-operator-less-than-or-equals-operator.md)|指出目前 VectorViewIterator 是否小於或等於指定的 VectorViewIterator。|  
|[VectorViewIterator::operator\-\= 運算子](../cppcx/vectorviewiterator-operator-subtract-assign-operator.md)|依指定的位移值遞減目前 VectorViewIterator。|  
|[VectorViewIterator::operator\=\= 運算子](../cppcx/vectorviewiterator-operator-equality-operator.md)|指出目前 VectorViewIterator 是否等於指定的 VectorViewIterator。|  
|[VectorViewIterator::operator\> 運算子](../cppcx/vectorviewiterator-operator-greater-than-operator.md)|指出目前 VectorViewIterator 是否大於指定的 VectorViewIterator。|  
|[VectorViewIterator::operator\-\> 運算子](../cppcx/vectorviewiterator-operator-arrow-operator.md)|擷取目前 VectorViewIterator 參考的元素的位址。|  
|[VectorViewIterator::operator\>\= 運算子](../cppcx/vectorviewiterator-operator-greater-than-or-equals-operator.md)|指出目前 VectorViewIterator 是否大於或等於指定的 VectorViewIterator。|  
  
## 繼承階層  
 `VectorViewIterator`  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)