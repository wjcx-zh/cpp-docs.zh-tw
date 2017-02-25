---
title: "priority_queue (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/queue> 標頭 [STL/CLR]"
  - "<queue> 標頭 [STL/CLR]"
  - "priority_queue 類別 [STL/CLR]"
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# priority_queue (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述物件控制存取項目的變更長度順序序列。  您使用容器配接器 `priority_queue` 處理基礎容器為優先權佇列。  
  
 在如下解譯， `GValue` 相當於 `Value` ，除非後面是參考型別，在這種情況下，它是 `Value^`的情況下。  同樣地，`GContainer` 與 `Container` ，除非後面是參考型別，在這種情況下，它是 `Container^`的情況下  
  
## 語法  
  
```  
template<typename Value,  
    typename Container>  
    ref class priority_queue  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>  
    { ..... };  
```  
  
#### 參數  
 值  
 受控制序列中項目的型別。  
  
 容器  
 基礎容器的型別。  
  
## 成員  
  
|類型定義|說明|  
|----------|--------|  
|[priority\_queue::const\_reference](../dotnet/priority-queue-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[priority\_queue::container\_type](../dotnet/priority-queue-container-type-stl-clr.md)|基礎容器的型別。|  
|[priority\_queue::difference\_type](../dotnet/priority-queue-difference-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[priority\_queue::generic\_container](../dotnet/priority-queue-generic-container-stl-clr.md)|泛型介面的型別的容器配接器。|  
|[priority\_queue::generic\_value](../dotnet/priority-queue-generic-value-stl-clr.md)|容器適配器的泛型介面的元素的型別。|  
|[priority\_queue::reference](../dotnet/priority-queue-reference-stl-clr.md)|項目的參考類型。|  
|[priority\_queue::size\_type](../dotnet/priority-queue-size-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[priority\_queue::value\_compare](../dotnet/priority-queue-value-compare-stl-clr.md)|兩個項目的排序委派。|  
|[priority\_queue::value\_type](../dotnet/priority-queue-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[priority\_queue::assign](../dotnet/priority-queue-assign-stl-clr.md)|取代所有項目。|  
|[priority\_queue::empty](../dotnet/priority-queue-empty-stl-clr.md)|測試項目是否不存在。|  
|[priority\_queue::get\_container](../dotnet/priority-queue-get-container-stl-clr.md)|存取基礎容器。|  
|[priority\_queue::pop](../dotnet/priority-queue-pop-stl-clr.md)|移除 hghest 優先順序項目。|  
|[priority\_queue::priority\_queue](../dotnet/priority-queue-priority-queue-stl-clr.md)|建構一個容器物件。|  
|[priority\_queue::push](../dotnet/priority-queue-push-stl-clr.md)|加入新增項目|  
|[priority\_queue::size](../dotnet/priority-queue-size-stl-clr.md)|計數項目的數目。|  
|[priority\_queue::top](../dotnet/priority-queue-top-stl-clr.md)|存取最高優先權的項目。|  
|[priority\_queue::to\_array](../dotnet/priority-queue-to-array-stl-clr.md)|複製受控制序列到新陣列。|  
|[priority\_queue::value\_comp](../dotnet/priority-queue-value-comp-stl-clr.md)|複製兩個項目的排序委派。|  
  
|屬性|說明|  
|--------|--------|  
|[priority\_queue::top\_item](../dotnet/priority-queue-top-item-stl-clr.md)|存取最高優先權的項目。|  
  
|運算子|說明|  
|---------|--------|  
|[priority\_queue::operator\=](../dotnet/priority-queue-operator-assign-stl-clr.md)|取代受控制序列。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.ICloneable>|重複物件。|  
|IPriorityQueue\<Value, Container\>|維護泛型容器配接器。|  
  
## 備註  
 物件配置和未使用的記憶體區域透過基礎容器的序列，型別控制 `Container`，儲存 `Value` 項目並增加在要求時。  它保留順序排列成堆積，與可移動最高優先權的項目 \(頂端\) 項目立即存取和。  物件會限制對推入新項目和快顯最高優先權的項目的存取，實作優先權佇列。  
  
 它會藉由呼叫 [priority\_queue::value\_compare](../dotnet/priority-queue-value-compare-stl-clr.md)型別所儲存的委派物件控制物件的排序序列。  在建構 priority\_queue 時，您可以指定儲存委派物件;如果您不指定委派物件，預設為比較 `operator<(value_type, value_type)`。  您可以呼叫成員函式存取這個儲存物件的`()`[priority\_queue::value\_comp](../dotnet/priority-queue-value-comp-stl-clr.md)。  
  
 這類委派物件必須強制嚴格弱式順序給 [priority\_queue::value\_type](../dotnet/priority-queue-value-type-stl-clr.md)型別的值。  這表示，任何兩個索引鍵的 `X` 和 `Y`:  
  
 `value_comp()(X, Y)` 會在每次呼叫相同的布林值結果。  
  
 如果 `value_comp()(X, Y)` 為 true，則 `value_comp()(Y, X)` 必須為 false。  
  
 如果 `value_comp()(X, Y)` 為 true，則 `X` 會在 `Y`之前。  
  
 如果 `!value_comp()(X, Y) && !value_comp()(Y, X)` 為 true，則 `X` 和 `Y` 有相同 Bucket 的項目。  
  
 對於在受控制序列的 `Y` 之前的任何項目則為 `X` ， `key_comp()(Y, X)` 是錯誤的。\(預設委派物件，金鑰會減少值\)。  
  
 最高優先權的項目而不是在其他項目之前已排序的其中一個項目。  
  
 因為基礎容器保留項目順序為堆積:  
  
 容器必須支援隨機存取 Iterator。  
  
 與相等排序的項目比它們已推入可能以不同的順序快顯。\(定序不穩定\)。  
  
 因此，基礎容器的候選包括 [deque](../dotnet/deque-stl-clr.md) 和 [向量](../dotnet/vector-stl-clr.md)。  
  
## 需求  
 **標頭：** \<cliext\/queue\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [堆疊](../dotnet/stack-stl-clr.md)   
 [向量](../dotnet/vector-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)