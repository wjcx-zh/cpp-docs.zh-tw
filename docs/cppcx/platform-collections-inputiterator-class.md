---
title: "Platform::Collections::InputIterator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::InputIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InputIterator 類別"
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::Collections::InputIterator 類別
為衍生自 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 的集合提供標準樣板程式庫 InputIterator。  
  
## 語法  
  
```  
template <  
   typename X  
>  
class InputIterator;  
```  
  
#### 參數  
 `X`  
 InputIterator 樣板類別的 typename。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`difference_type`|指標差異 \(ptrdiff\_t\)。|  
|`iterator_category`|輸入迭代器的類別 \(::std::input\_iterator\_tag\)。|  
|`pointer`|`const` `X` 的指標|  
|`reference`|`const` `X` 的參考|  
|`value_type`|`X` typename。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[InputIterator::InputIterator 建構函式](../cppcx/inputiterator-inputiterator-constructor.md)|初始化 InputIterator 類別的新執行個體。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[InputIterator::operator\!\= 運算子](../cppcx/inputiterator-operator-inequality-operator.md)|指出目前 InputIterator 是否不等於指定的 InputIterator。|  
|[InputIterator::operator\* 運算子](../cppcx/inputiterator-operator-decrementoperator.md)|擷取目前 InputIterator 指定之項目的參考。|  
|[InputIterator::operator\+\+ 運算子](../cppcx/inputiterator-operator-increment-operator.md)|遞增目前 InputIterator。|  
|[InputIterator::operator\=\= 運算子](../cppcx/inputiterator-operator-equality-operator.md)|指出目前 InputIterator 是否等於指定的 InputIterator。|  
|[InputIterator::operator\-\> 運算子](../cppcx/inputiterator-operator-arrow-operator.md)|擷取目前 InputIterator 參考的項目位址。|  
  
## 繼承階層  
 `InputIterator`  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)