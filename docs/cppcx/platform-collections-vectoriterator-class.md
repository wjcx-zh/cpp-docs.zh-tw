---
title: "Platform::Collections::VectorIterator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator 類別"
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Collections::VectorIterator 類別
為衍生自 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] IVector 介面的物件提供標準樣板程式庫迭代器。  
  
 VectorIterator 這個 Proxy 迭代器可以儲存類型為 VectorProxy\<T\> 的元素。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## 語法  
  
```  
template <  
   typename T  
>  
class VectorIterator;  
```  
  
#### 參數  
 `T`  
 VectorIterator 樣板類別的 typename。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`difference_type`|指標差異 \(ptrdiff\_t\)。|  
|`iterator_category`|隨機存取迭代器的分類 \(::std::random\_access\_iterator\_tag\)。|  
|`pointer`|VectorIterator 實作所需的 Platform::Collections::Details::VectorProxy\<T\> 內部類型指標。|  
|`reference`|VectorIterator 實作所需的 Platform::Collections::Details::VectorProxy\<T\> 內部類型參考。|  
|`value_type`|`T` typename。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[VectorIterator::VectorIterator 建構函式](../cppcx/vectoriterator-vectoriterator-constructor.md)|初始化 VectorIterator 類別的新執行個體。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[VectorIterator::operator\- 運算子](../cppcx/vectoriterator-operator-minus-operator.md)|從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。|  
|[VectorIterator::operator\-\- 運算子](../cppcx/vectoriterator-operator-decrement-operator.md)|遞減目前 VectorIterator。|  
|[VectorIterator::operator\!\= 運算子](../cppcx/vectoriterator-operator-inequality-operator.md)|指出目前 VectorIterator 是否不等於指定的 VectorIterator。|  
|[VectorIterator::operator\* 運算子](../cppcx/vectoriterator-operator-dereference-operator.md)|擷取目前 VectorIterator 指定之元素的參考。|  
|[VectorIterator::operatorOperator](../cppcx/vectoriterator-operatoroperator.md)|擷取從目前 VectorIterator 開始指定偏移的元素的參考。|  
|[\(刪除\) VectorIterator::operator\+ 運算子](http://msdn.microsoft.com/zh-tw/b0b1af2c-e2a8-4876-99dc-7351bfc46ce4)|傳回 VectorIterator ，參考從指定的 VectorIterator 開始指定位移的項目。|  
|[VectorIterator::operator\+\+ 運算子](../cppcx/vectoriterator-operator-increment-operator.md)|遞增目前 VectorIterator。|  
|[VectorIterator::operator\+\= 運算子](../cppcx/vectoriterator-operator-plus-assign-operator.md)|依指定的位移值遞增目前 VectorIterator。|  
|[VectorIterator::operator\< 運算子](../cppcx/vectoriterator-operator-less-than-operator.md)|指出目前 VectorIterator 是否小於指定的 VectorIterator。|  
|[VectorIterator::operator\<\= 運算子](../cppcx/vectoriterator-operator-less-than-or-equals-operator.md)|指出目前 VectorIterator 是否小於或等於指定的 VectorIterator。|  
|[VectorIterator::operator\-\= 運算子](../cppcx/vectoriterator-operator-subtract-assign-operator.md)|依指定的位移遞減目前 VectorIterator。|  
|[VectorIterator::operator\=\= 運算子](../cppcx/vectoriterator-operator-equality-operator.md)|指出目前 VectorIterator 是否等於指定的 VectorIterator。|  
|[VectorIterator::operator\> 運算子](../cppcx/vectoriterator-operator-greater-than-operator.md)|指出目前 VectorIterator 是否大於指定的 VectorIterator。|  
|[VectorIterator::operator\-\> 運算子](../cppcx/vectoriterator-operator-arrow-operator.md)|擷取目前 VectorIterator 參考的元素的位址。|  
|[VectorIterator::operator\>\= 運算子](../cppcx/vectoriterator-operator-greater-than-or-equal-operator.md)|指出目前 VectorIterator 是否大於或等於指定的 VectorIterator。|  
  
## 繼承階層  
 `VectorIterator`  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)