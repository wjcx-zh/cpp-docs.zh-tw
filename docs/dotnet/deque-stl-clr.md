---
title: "deque (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/deque> 標頭 [STL/CLR]"
  - "<deque> 標頭 [STL/CLR]"
  - "deque 類別 [STL/CLR]"
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# deque (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述物件控制項有隨機存取項目的變更長度序列。  您使用容器 `deque` 處理看起來像儲存連續區塊，不過，可以放大或縮小在任一端，而不需要複製其餘項目的序列。  因此可以有效地實作 `double-ended queue`。\(因此名稱\)。  
  
 在如下解譯， `GValue` 相當於 `Value` ，除非後面是參考型別，在這種情況下，它是 `Value^`的情況下。  
  
## 語法  
  
```  
template<typename Value>  
    ref class deque  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IDeque<GValue>  
    { ..... };  
```  
  
#### 參數  
 G 值  
 項目的泛型型別在受控制序列的。  
  
 值  
 受控制序列中項目的型別。  
  
## 成員  
  
|型別定義|說明|  
|----------|--------|  
|[deque::const\_iterator](../dotnet/deque-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[deque::const\_reference](../dotnet/deque-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[deque::const\_reverse\_iterator](../dotnet/deque-const-reverse-iterator-stl-clr.md)|常數反向 Iterator 的型別受控制序列的。|  
|[deque::difference\_type](../dotnet/deque-difference-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[deque::generic\_container](../dotnet/deque-generic-container-stl-clr.md)|泛型介面的型別的容器。|  
|[deque::generic\_iterator](../dotnet/deque-generic-iterator-stl-clr.md)|Iterator 的型別泛型介面的容器。|  
|[deque::generic\_reverse\_iterator](../dotnet/deque-generic-reverse-iterator-stl-clr.md)|反向 Iterator 的型別泛型介面的容器。|  
|[deque::generic\_value](../dotnet/deque-generic-value-stl-clr.md)|項目的型別泛型介面的容器。|  
|[deque::iterator](../dotnet/deque-iterator-stl-clr.md)|受控制序列中 iterator 的類型。|  
|[deque::reference](../dotnet/deque-reference-stl-clr.md)|項目的參考類型。|  
|[deque::reverse\_iterator](../dotnet/deque-reverse-iterator-stl-clr.md)|反向 Iterator 的型別受控制序列的。|  
|[deque::size\_type](../dotnet/deque-size-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[deque::value\_type](../dotnet/deque-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[deque::assign](../dotnet/deque-assign-stl-clr.md)|取代所有項目。|  
|[deque::at](../dotnet/deque-at-stl-clr.md)|存取項目在指定的位置。|  
|[deque::back](../dotnet/deque-back-stl-clr.md)|存取最後一個項目。|  
|[deque::begin](../dotnet/deque-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[deque::clear](../dotnet/deque-clear-stl-clr.md)|移除所有項目。|  
|[deque::deque](../dotnet/deque-deque-stl-clr.md)|建構一個容器物件。|  
|[deque::empty](../dotnet/deque-empty-stl-clr.md)|測試項目是否不存在。|  
|[deque::end](../dotnet/deque-end-stl-clr.md)|指定受控制序列的結尾。|  
|[deque::erase](../dotnet/deque-erase-stl-clr.md)|移除指定位置的項目。|  
|[deque::front](../dotnet/deque-front-stl-clr.md)|存取第一個項目。|  
|[deque::insert](../dotnet/deque-insert-stl-clr.md)|將項目在指定的位置。|  
|[deque::pop\_back](../dotnet/deque-pop-back-stl-clr.md)|移除最後一個項目。|  
|[deque::pop\_front](../dotnet/deque-pop-front-stl-clr.md)|移除第一個項目。|  
|[deque::push\_back](../dotnet/deque-push-back-stl-clr.md)|將新的最後一個項目。|  
|[deque::push\_front](../dotnet/deque-push-front-stl-clr.md)|將新的第一個項目。|  
|[deque::rbegin](../dotnet/deque-rbegin-stl-clr.md)|指定已還原的受控制序列開頭。|  
|[deque::rend](../dotnet/deque-rend-stl-clr.md)|指定已還原的受控制序列結尾。|  
|[deque::resize](../dotnet/deque-resize-stl-clr.md)|變更項目的數目。|  
|[deque::size](../dotnet/deque-size-stl-clr.md)|計數項目的數目。|  
|[deque::swap](../dotnet/deque-swap-stl-clr.md)|交換兩個容器的內容。|  
|[deque::to\_array](../dotnet/deque-to-array-stl-clr.md)|複製受控制序列的新陣列。|  
  
|屬性|說明|  
|--------|--------|  
|[deque::back\_item](../dotnet/deque-back-item-stl-clr.md)|存取最後一個項目。|  
|[deque::front\_item](../dotnet/deque-front-item-stl-clr.md)|存取第一個項目。|  
  
|運算子|說明|  
|---------|--------|  
|[deque::operator\!\=](../dotnet/deque-operator-inequality-stl-clr.md)|判斷兩個 `deque` 物件是否不相等。|  
|[deque::operator](../dotnet/deque-operator-stl-clr.md)|存取項目在指定的位置。|  
|[operator\< \(deque\)](../dotnet/operator-less-than-deque-stl-clr.md)|判斷 `deque` 物件是否小於另一個 `deque` 物件。|  
|[operator\<\= \(deque\)](../dotnet/operator-less-or-equal-deque-stl-clr.md)|判斷 `deque` 物件是否小於或等於另一個 `deque` 物件。|  
|[operator\= \(deque\)](../dotnet/operator-assign-deque-stl-clr.md)|取代受控制序列。|  
|[operator\=\= \(deque\)](../dotnet/operator-equality-deque-stl-clr.md)|判斷 `deque` 物件是否等於另一個 `deque` 物件。|  
|[operator\> \(deque\)](../dotnet/operator-greater-than-deque-stl-clr.md)|判斷 `deque` 物件是否大於另一個 `deque` 物件。|  
|[operator\>\= \(deque\)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)|判斷 `deque` 物件是否大於或等於另一個 `deque` 物件。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.ICloneable>|複製物件。|  
|<xref:System.Collections.IEnumerable>|序列傳遞項目。|  
|<xref:System.Collections.ICollection>|維護項目的群組。|  
|<xref:System.Collections.Generic.IEnumerable%601>|序列傳遞型別項目。|  
|<xref:System.Collections.Generic.ICollection%601>|維護型別項目的群組。|  
|<xref:System.Collections.Generic.IList%601>|maintain 排序的型別項目的群組。|  
|IDequeValue\<\>|維護泛型容器。|  
  
## 備註  
 物件配置和未使用的記憶體區域會將儲存的一些控制項指定 `Value` 項目區塊的序列。  陣列成長需求。  成長發生，在這種情況下預先規劃或附加新項目的代價是常數時間，，其餘項目不會干擾。  您也可以移除項目在任一端在常數時間而不干擾其餘項目。  因此，雙向佇列是基礎容器的候選樣板類別 [queue](../dotnet/queue-stl-clr.md) 或樣板類別的 [堆疊](../dotnet/stack-stl-clr.md)。  
  
 `deque` 物件支援隨機存取 Iterator，這表示您可以參考項目直接寫入其位置數值，計算以零第一個 \(最上層\) 項目，最後 \(後面\) [deque::size](../dotnet/deque-size-stl-clr.md)項目的`() - 1` 。  這也表示雙向佇列是基礎容器的候選樣板類別的 [priority\_queue](../dotnet/priority-queue-stl-clr.md)。  
  
 雙向 Iterator 佇列儲存控制代碼關聯的雙向佇列物件，其指定這個項目的偏差。  您只能使用 Iterator 與其關聯的容器物件。  雙向佇列項目的偏差必要是 `not` 與其位置相同。  插入的第一個項目具有不壓縮零，則下附加的項目不會有 1，不過，這個下前面的項目不會有 \-1。  
  
 插入或清除項目在任一端做修改 `not` 項目的值會儲存在任何有效的偏差。  插入或清除內部項目，不過， `can` 變更項目值儲存在指定的偏差，因此， Iterator 的值可能也會變更。\(容器可能必須上下複製元素在插入之前先建立空白或在清除之後填滿空白\)。不過，，只要它的偏差指定有效的項目，在佇列中保持有效。  而且，有效 Iterator 保持 dereferencable\-\-您可以使用它所指派它存取或修改項目的值\-\-只要的偏差不等於 `end()`所傳回的 Iterator 的偏差。  
  
 清除或移除元素呼叫它的儲存值的解構函式。  終結容器清除所有項目。  因此，項目型別是 ref 類別的容器確保項目不使用得比容器的。  請注意，然而，容器控制碼做 `not` 終結的項目。  
  
## 需求  
 **標題:** \<cliext\/雙向佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [堆疊](../dotnet/stack-stl-clr.md)   
 [向量](../dotnet/vector-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)