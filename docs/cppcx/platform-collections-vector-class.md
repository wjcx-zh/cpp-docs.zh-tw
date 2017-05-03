---
title: "Platform::Collections::Vector 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector 類別 (C++/Cx)"
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 17
---
# Platform::Collections::Vector 類別
表示可依索引來個別存取的物件序列集合。  
  
## 語法  
  
```  
template <typename T, typename E>  
   ref class Vector sealed;  
```  
  
#### 參數  
 `T`  
 Vector 物件中包含的元素型別。  
  
 `E`  
 指定二元述詞，以測試是否與 `T` 型別的值相等。 預設值是 `std::equal_to<T>`。  
  
## 備註  
 可使用的型別如下：  
  
1.  整數  
  
2.  介面類別 ^  
  
3.  公用 ref 類別^  
  
4.  value struct  
  
5.  公用列舉類別  
  
 Vector 類別是 [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) 介面的 C\+\+ 具象實作。  
  
 如果您嘗試在公用傳回值或參數中使用 Vector 型別，則會引發編譯器錯誤 C3986。 您可以將參數或傳回值類型變更為 [Windows::Foundation::Collections::IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) 來修正錯誤。 如需詳細資訊，請參閱[集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[Vector::Vector 建構函式](../cppcx/vector-vector-constructor.md)|初始化 Vector 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[Vector::Append 方法](../cppcx/vector-append-method.md)|在目前 Vector 的最後一個項目之後插入指定的項目。|  
|[Vector::Clear 方法](../cppcx/vector-clear-method.md)|刪除目前 Vector 的所有項目。|  
|[Vector::First 方法](../cppcx/vector-first-method.md)|傳回迭代器，指定 Vector 中的第一個項目。|  
|[Vector::GetAt 方法](../cppcx/vector-getat-method.md)|擷取由指定之索引所識別的目前 Vector 項目。|  
|[Vector::GetMany 方法](../cppcx/vector-getmany-method.md)|從目前 Vector 中，由指定的索引處開始，擷取一連串項目。|  
|[Vector::GetView 方法](../cppcx/vector-getview-method.md)|傳回 Vector 的唯讀檢視，也就是 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)。|  
|[Vector::IndexOf 方法](../cppcx/vector-indexof-method.md)|在目前 Vector 中搜尋指定的項目，如果找到，則傳回項目的索引。|  
|[Vector::InsertAt 方法](../cppcx/vector-insertat-method.md)|將指定的項目插入至目前 Vector 中，指定之索引所識別項目的後面。|  
|[Vector::ReplaceAll 方法](../cppcx/vector-replaceall-method.md)|刪除目前 Vector 中的元素，然後從指定的陣列插入元素。|  
|[Vector::RemoveAt 方法](../cppcx/vector-removeat-method.md)|從目前向量中刪除指定索引所識別的元素。|  
|[Vector::RemoveAtEnd 方法](../cppcx/vector-removeatend-method.md)|刪除目前 Vector 結尾處的項目。|  
|[Vector::SetAt 方法](../cppcx/vector-setat-method.md)|在目前 Vector 中，將指定的值指派給由指定的索引所識別的元素。|  
|[Vector::Size 方法](../cppcx/vector-size-method.md)|傳回目前 Vector 物件中的項目數。|  
  
### 事件  
  
|||  
|-|-|  
|名稱|描述|  
|事件 [Windows::Foundation::Collection::VectorChangedEventHandler\<T\>^ VectorChanged](http://go.microsoft.com/fwlink/p/?LinkId=262644)|Vector 變更時發生。|  
  
## 繼承階層  
 `Vector`  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [\(NOTINBUILD\) Platform 命名空間](http://msdn.microsoft.com/zh-tw/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)   
 [在 C\+\+ 中建立 Windows 執行階段元件](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)