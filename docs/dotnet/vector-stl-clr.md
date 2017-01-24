---
title: "vector (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/vector> 標頭 [STL/CLR]"
  - "<vector> 標頭 [STL/CLR]"
  - "vector 類別 [STL/CLR]"
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述物件控制項有隨機存取項目的變更長度序列。  您使用容器 `vector` 處理項目序列做為儲存連續區塊。  區塊會實作為成長需求的陣列。  
  
 在如下解譯， `GValue` 相當於 `Value` ，除非後面是參考型別，在這種情況下，它是 `Value^`的情況下。  
  
## 語法  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
#### 參數  
 值  
 受控制序列中項目的型別。  
  
## 成員  
  
|型別定義|說明|  
|----------|--------|  
|[vector::const\_iterator](../dotnet/vector-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[vector::const\_reference](../dotnet/vector-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[vector::const\_reverse\_iterator](../dotnet/vector-const-reverse-iterator-stl-clr.md)|常數反向 Iterator 的型別受控制序列的。|  
|[vector::difference\_type](../dotnet/vector-difference-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[vector::generic\_container](../dotnet/vector-generic-container-stl-clr.md)|泛型介面的型別的容器。|  
|[vector::generic\_iterator](../dotnet/vector-generic-iterator-stl-clr.md)|Iterator 的型別泛型介面的容器。|  
|[vector::generic\_reverse\_iterator](../dotnet/vector-generic-reverse-iterator-stl-clr.md)|反向 Iterator 的型別泛型介面的容器。|  
|[vector::generic\_value](../dotnet/vector-generic-value-stl-clr.md)|項目的型別泛型介面的容器。|  
|[vector::iterator](../dotnet/vector-iterator-stl-clr.md)|受控制序列中 iterator 的類型。|  
|[vector::reference](../dotnet/vector-reference-stl-clr.md)|項目的參考類型。|  
|[vector::reverse\_iterator](../dotnet/vector-reverse-iterator-stl-clr.md)|反向 Iterator 的型別受控制序列的。|  
|[vector::size\_type](../dotnet/vector-size-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[vector::value\_type](../dotnet/vector-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[vector::assign](../dotnet/vector-assign-stl-clr.md)|取代所有項目。|  
|[vector::at](../dotnet/vector-at-stl-clr.md)|存取項目在指定的位置。|  
|[vector::back](../dotnet/vector-back-stl-clr.md)|存取最後一個項目。|  
|[vector::begin](../dotnet/vector-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[vector::capacity](../dotnet/vector-capacity-stl-clr.md)|報告容器配置儲存區的大小。|  
|[vector::clear](../dotnet/vector-clear-stl-clr.md)|移除所有項目。|  
|[vector::empty](../dotnet/vector-empty-stl-clr.md)|測試項目是否不存在。|  
|[vector::end](../dotnet/vector-end-stl-clr.md)|指定受控制序列的結尾。|  
|[vector::erase](../dotnet/vector-erase-stl-clr.md)|移除指定位置的項目。|  
|[vector::front](../dotnet/vector-front-stl-clr.md)|存取第一個項目。|  
|[vector::insert](../dotnet/vector-insert-stl-clr.md)|將項目在指定的位置。|  
|[vector::pop\_back](../dotnet/vector-pop-back-stl-clr.md)|移除最後一個項目。|  
|[vector::push\_back](../dotnet/vector-push-back-stl-clr.md)|將新的最後一個項目。|  
|[vector::rbegin](../dotnet/vector-rbegin-stl-clr.md)|指定已還原的受控制序列開頭。|  
|[vector::rend](../dotnet/vector-rend-stl-clr.md)|指定已還原的受控制序列結尾。|  
|[vector::reserve](../dotnet/vector-reserve-stl-clr.md)|確保容器的最小成長容量。|  
|[vector::resize](../dotnet/vector-resize-stl-clr.md)|變更項目的數目。|  
|[vector::size](../dotnet/vector-size-stl-clr.md)|計數項目的數目。|  
|[vector::swap](../dotnet/vector-swap-stl-clr.md)|交換兩個容器的內容。|  
|[vector::to\_array](../dotnet/vector-to-array-stl-clr.md)|複製受控制序列的新陣列。|  
|[vector::vector](../dotnet/vector-vector-stl-clr.md)|建構一個容器物件。|  
  
|屬性|說明|  
|--------|--------|  
|[vector::back\_item](../dotnet/vector-back-item-stl-clr.md)|存取最後一個項目。|  
|[vector::front\_item](../dotnet/vector-front-item-stl-clr.md)|存取第一個項目。|  
  
|運算子|說明|  
|---------|--------|  
|[vector::operator\=](../dotnet/vector-operator-assign-stl-clr.md)|取代受控制序列。|  
|[vector::operator](../dotnet/vector-operator-stl-clr.md)|存取項目在指定的位置。|  
|[operator\!\= \(vector\)](../dotnet/operator-inequality-vector-stl-clr.md)|判斷 `vector` 物件是否不等於另一個 `vector` 物件。|  
|[operator\< \(vector\)](../dotnet/operator-less-than-vector-stl-clr.md)|判斷 `vector` 物件是否小於另一個 `vector` 物件。|  
|[operator\<\= \(vector\)](../dotnet/operator-less-or-equal-vector-stl-clr.md)|判斷 `vector` 物件是否小於或等於另一個 `vector` 物件。|  
|[operator\=\= \(vector\)](../dotnet/operator-equality-vector-stl-clr.md)|判斷 `vector` 物件是否等於另一個 `vector` 物件。|  
|[operator\> \(vector\)](../dotnet/operator-greater-than-vector-stl-clr.md)|判斷 `vector` 物件是否大於另一個 `vector` 物件。|  
|[operator\>\= \(vector\)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)|判斷 `vector` 物件是否大於或等於另一個 `vector` 物件。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.ICloneable>|複製物件。|  
|<xref:System.Collections.IEnumerable>|序列傳遞項目。|  
|<xref:System.Collections.ICollection>|維護項目的群組。|  
|<xref:System.Collections.Generic.IEnumerable%601>|序列傳遞型別項目。|  
|<xref:System.Collections.Generic.ICollection%601>|維護型別項目的群組。|  
|<xref:System.Collections.Generic.IList%601>|maintain 排序的型別項目的群組。|  
|IVectorValue\<\>|維護泛型容器。|  
  
## 備註  
 物件配置和未使用的記憶體區域它可以儲存的 `Value` 控制項項目，成長需求的序列。  成長發生，在此情況下附加新項目的成本會為舊常數時間。  換句話說，，因為受控制序列的長度變得更大，加入至這個結尾的項目的成本不增加，平均。  因此，向量是基礎容器的候選樣板類別的 [堆疊](../dotnet/stack-stl-clr.md)。  
  
 `vector` 支援隨機存取 Iterator，這表示您可以參考項目直接寫入其位置數值，計算以零第一個 \(最上層\) 項目，最後 \(後面\) [vector::size](../dotnet/vector-size-stl-clr.md)項目的`() - 1` 。  這也表示向量是基礎容器的候選樣板類別的 [priority\_queue](../dotnet/priority-queue-stl-clr.md)。  
  
 向量中儲存的控制代碼關聯的向量物件，其指定這個項目的偏差。  您只能使用 Iterator 與其關聯的容器物件。  向量偏差的項目會與其位置。  
  
 插入或清除項目可以變更項目值儲存在指定的位置，因此， Iterator 的值可能也會變更。\(容器可能必須上下複製元素在插入之前先建立空白或在清除之後填滿空白\)。不過，，只要它的偏差介於 `[0,`[vector::size](../dotnet/vector-size-stl-clr.md)`()]`，向量 Iterator 保持有效。  而且，有效 Iterator 保持 dereferencable\-\-您可以使用它所指派它存取或修改項目的值\-\-只要的偏差不等於 `size()`。  
  
 清除或移除元素呼叫它的儲存值的解構函式。  終結容器清除所有項目。  因此，項目型別是 ref 類別的容器確保項目不使用得比容器的。  請注意，然而，容器控制碼做 `not` 終結的項目。  
  
## 需求  
 **標題:** \<cliext\/向量\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [堆疊](../dotnet/stack-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)