---
title: "list (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/list> 標頭 [STL/CLR]"
  - "<list> 標頭 [STL/CLR]"
  - "清單類別 [STL/CLR]"
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# list (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述物件控制存取雙向項目的變更長度序列。  您使用容器 `list` 處理項目序列做為節點雙向連結串列，每個儲存一個項目。  
  
 在如下解譯， `GValue` 相當於 `Value` ，除非後面是參考型別，在這種情況下，它是 `Value^`的情況下。  
  
## 語法  
  
```  
template<typename Value>  
    ref class list  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        Microsoft::VisualC::StlClr::IList<GValue>  
    { ..... };  
```  
  
#### 參數  
 值  
 受控制序列中項目的型別。  
  
## 成員  
  
|型別定義|說明|  
|----------|--------|  
|[list::const\_iterator](../dotnet/list-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[list::const\_reference](../dotnet/list-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[list::const\_reverse\_iterator](../dotnet/list-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[list::difference\_type](../dotnet/list-difference-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[list::generic\_container](../dotnet/list-generic-container-stl-clr.md)|泛型介面的型別的容器。|  
|[list::generic\_iterator](../dotnet/list-generic-iterator-stl-clr.md)|容器的泛型介面的迭代器的型別。|  
|[list::generic\_reverse\_iterator](../dotnet/list-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器的型別。|  
|[list::generic\_value](../dotnet/list-generic-value-stl-clr.md)|容器的泛型介面的元素的型別。|  
|[list::iterator](../dotnet/list-iterator-stl-clr.md)|受控制序列中 iterator 的類型。|  
|[list::reference](../dotnet/list-reference-stl-clr.md)|項目的參考類型。|  
|[list::reverse\_iterator](../dotnet/list-reverse-iterator-stl-clr.md)|用於受控制序列的反向迭代器類型。|  
|[list::size\_type](../dotnet/list-size-type-stl-clr.md)|兩個項目之間的帶正負號距離的類型。|  
|[list::value\_type](../dotnet/list-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[list::assign](../dotnet/list-assign-stl-clr.md)|取代所有項目。|  
|[list::back](../dotnet/list-back-stl-clr.md)|存取最後一個項目。|  
|[list::begin](../dotnet/list-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[list::clear](../dotnet/list-clear-stl-clr.md)|移除所有項目。|  
|[list::empty](../dotnet/list-empty-stl-clr.md)|測試項目是否不存在。|  
|[list::end](../dotnet/list-end-stl-clr.md)|指定受控制序列的結尾。|  
|[list::erase](../dotnet/list-erase-stl-clr.md)|移除指定位置的項目。|  
|[list::front](../dotnet/list-front-stl-clr.md)|存取第一個項目。|  
|[list::insert](../dotnet/list-insert-stl-clr.md)|將項目加至指定的位置。|  
|[list::list](../dotnet/list-list-stl-clr.md)|建構一個容器物件。|  
|[list::merge](../dotnet/list-merge-stl-clr.md)|合併兩個已排序的受控制序列。|  
|[list::pop\_back](../dotnet/list-pop-back-stl-clr.md)|移除最後一個項目。|  
|[list::pop\_front](../dotnet/list-pop-front-stl-clr.md)|移除第一個項目。|  
|[list::push\_back](../dotnet/list-push-back-stl-clr.md)|加入新的最後一個元素。|  
|[list::push\_front](../dotnet/list-push-front-stl-clr.md)|加入新的第一個項目。|  
|[list::rbegin](../dotnet/list-rbegin-stl-clr.md)|指定已還原的受控制序列開頭。|  
|[list::remove](../dotnet/list-remove-stl-clr.md)|移除具有指定的值的項目。|  
|[list::remove\_if](../dotnet/list-remove-if-stl-clr.md)|移除通過指定測試的項目。|  
|[list::rend](../dotnet/list-rend-stl-clr.md)|指定已還原的受控制序列結尾。|  
|[list::resize](../dotnet/list-resize-stl-clr.md)|變更項目的數目。|  
|[list::reverse](../dotnet/list-reverse-stl-clr.md)|反轉受控制序列。|  
|[list::size](../dotnet/list-size-stl-clr.md)|計數項目的數目。|  
|[list::sort](../dotnet/list-sort-stl-clr.md)|排序受控制序列。|  
|[list::splice](../dotnet/list-splice-stl-clr.md)|Restitches 節點之間的連結。|  
|[list::swap](../dotnet/list-swap-stl-clr.md)|交換兩個容器的內容。|  
|[list::to\_array](../dotnet/list-to-array-stl-clr.md)|複製受控制序列到新陣列。|  
|[list::unique](../dotnet/list-unique-stl-clr.md)|移除通過指定測試的相鄰項目。|  
  
|屬性|說明|  
|--------|--------|  
|[list::back\_item](../dotnet/list-back-item-stl-clr.md)|存取最後一個項目。|  
|[list::front\_item](../dotnet/list-front-item-stl-clr.md)|存取第一個項目。|  
  
|運算子|說明|  
|---------|--------|  
|[list::operator\=](../dotnet/list-operator-assign-stl-clr.md)|取代受控制序列。|  
|[operator\!\= \(list\)](../dotnet/operator-inequality-list-stl-clr.md)|判斷 `list` 物件是否不等於另一個 `list` 物件。|  
|[operator\< \(list\)](../dotnet/operator-less-than-list-stl-clr.md)|判斷 `list` 物件是否小於另一個 `list` 物件。|  
|[operator\<\= \(list\)](../dotnet/operator-less-or-equal-list-stl-clr.md)|判斷 `list` 物件是否小於或等於另外一個 `list` 物件。|  
|[operator\=\= \(list\)](../dotnet/operator-equality-list-stl-clr.md)|判斷 `list` 物件是否等於另一個 `list` 物件。|  
|[operator\> \(list\)](../dotnet/operator-greater-than-list-stl-clr.md)|判斷 `list` 物件是否大於另一個 `list` 物件。|  
|[operator\>\= \(list\)](../dotnet/operator-greater-or-equal-list-stl-clr.md)|判斷 `list` 物件是否大於或等於另外一個 `list` 物件。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.ICloneable>|重複物件。|  
|<xref:System.Collections.IEnumerable>|序列傳遞項目。|  
|<xref:System.Collections.ICollection>|維護項目的群組。|  
|<xref:System.Collections.Generic.IEnumerable%601>|序列傳遞型別項目。|  
|<xref:System.Collections.Generic.ICollection%601>|維護型別項目的群組。|  
|IList\<Value\>|維護泛型容器。|  
  
## 備註  
 物件配置和未使用的記憶體區域的控制項會以個別節點在雙向連結串列的序列。  它可以用修改節點之間的連結的方式重新排列項目，絕不會透過複製的節點內容到另一個。  這表示您可以自由地插入和移除項目，而不會干擾其他項目。  因此，清單是類別 [queue](../dotnet/queue-stl-clr.md) 或樣板類別的 [堆疊](../dotnet/stack-stl-clr.md) 的基礎容器候選樣板。  
  
 `list` 物件支援雙向迭代器，這表示您可以逐步執行至指定的相鄰項目的迭代器在受控制序列的項目。  特殊前端節點對應於 [list::end](../dotnet/list-end-stl-clr.md)所傳回的 Iterator`()`。  如果您以這個 Iterator 到達受控制序列的最後一個項目。  您可以增加清單迭代器以到達前端節點，因此，它與 `end()`會比較是否相等。  但是，您無法取值 `end()`所傳回的 Iterator。  
  
 請注意您無法直接參考指定的清單元素其數值位置\-\-該要求隨機存取 Iterator。  因此清單是 `not` 能用以作為 [priority\_queue](../dotnet/priority-queue-stl-clr.md)的基礎容器樣板類別。  
  
 清單迭代器中儲存關聯的清單節點的控制代碼，接著儲存的控制代碼關聯的容器。  您只能使用 Iterator 與其關聯的容器物件。  只要其關聯的清單節點與某一個清單相關連，清單迭代器保持有效。  而且，有效 Iterator dereferencable\-\-您可以使用它所指派它存取或修改項目的值\-\-只要不等於 `end()`。  
  
 清除或移除元素呼叫它的儲存值的解構函式。  終結容器清除所有項目。  因此，項目型別是 ref 類別的容器確保項目不使用得比容器的。  請注意，然而，容器控制碼做 `not` 終結的項目。  
  
## 需求  
 **標頭 ：** \<cliext\/list\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [堆疊](../dotnet/stack-stl-clr.md)   
 [向量](../dotnet/vector-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)