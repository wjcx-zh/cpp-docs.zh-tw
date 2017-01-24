---
title: "multimap (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/map> 標頭 [STL/CLR]"
  - "<map> 標頭 [STL/CLR]"
  - "multimap 類別 [STL/CLR]"
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述一個物件，其控制一個可雙向存取項目的變更長度序列。  您使用容器 `multimap` 處理項目序列，做為 \(幾乎\) 平衡且排序的樹，其每個節點儲存一個項目。  一個項目包含索引鍵 \(用以序列的排序\) 和對應的值 \(依乘巡配置\)。  
  
 在以下的敘述， `GValue` 和以下相同：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey` 與 `Key` 相同，除非後者是參考型別，在這種情況下，它是 `Key^`  
  
 `GMapped` 與 `Mapped` 相同，除非後者是參考型別，在這種情況下，它是 `Mapped^`  
  
## 語法  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class multimap  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
#### 參數  
 Key  
 受控制序列中項目的主要元件型別。  
  
 Mapped  
 受控制序列中項目的額外元件型別。  
  
## 成員  
  
|型別定義|說明|  
|----------|--------|  
|[multimap::const\_iterator](../dotnet/multimap-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[multimap::const\_reference](../dotnet/multimap-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[multimap::const\_reverse\_iterator](../dotnet/multimap-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器型別。|  
|[multimap::difference\_type](../dotnet/multimap-difference-type-stl-clr.md)|兩個項目之間的 \(可能帶正負號\) 距離的型別。|  
|[multimap::generic\_container](../dotnet/multimap-generic-container-stl-clr.md)|容器的泛型介面的型別。|  
|[multimap::generic\_iterator](../dotnet/multimap-generic-iterator-stl-clr.md)|容器的泛型介面的迭代器的型別。|  
|[multimap::generic\_reverse\_iterator](../dotnet/multimap-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器的型別。|  
|[multimap::generic\_value](../dotnet/multimap-generic-value-stl-clr.md)|容器的泛型介面的元素的型別。|  
|[multimap::iterator](../dotnet/multimap-iterator-stl-clr.md)|受控制序列中 iterator 的類型。|  
|[multimap::key\_compare](../dotnet/multimap-key-compare-stl-clr.md)|兩個金鑰的排序委派。|  
|[multimap::key\_type](../dotnet/multimap-key-type-stl-clr.md)|排序索引鍵的類型。|  
|[multimap::mapped\_type](../dotnet/multimap-mapped-type-stl-clr.md)|與每個索引鍵關聯的對應值型別。|  
|[multimap::reference](../dotnet/multimap-reference-stl-clr.md)|項目的參考類型。|  
|[multimap::reverse\_iterator](../dotnet/multimap-reverse-iterator-stl-clr.md)|用於受控制序列的反向迭代器型別。|  
|[multimap::size\_type](../dotnet/multimap-size-type-stl-clr.md)|兩個項目之間的 \(非負數\) 距離的型別。|  
|[multimap::value\_compare](../dotnet/multimap-value-compare-stl-clr.md)|兩個項目值的排序委派。|  
|[multimap::value\_type](../dotnet/multimap-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[multimap::begin](../dotnet/multimap-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[multimap::clear](../dotnet/multimap-clear-stl-clr.md)|移除所有項目。|  
|[multimap::count](../dotnet/multimap-count-stl-clr.md)|計算符合指定索引鍵的項目。|  
|[multimap::empty](../dotnet/multimap-empty-stl-clr.md)|測試是否不存在項目。|  
|[multimap::end](../dotnet/multimap-end-stl-clr.md)|指定受控制序列的結尾。|  
|[multimap::equal\_range](../dotnet/multimap-equal-range-stl-clr.md)|尋找符合指定索引鍵的範圍。|  
|[multimap::erase](../dotnet/multimap-erase-stl-clr.md)|移除指定位置的項目。|  
|[multimap::find](../dotnet/multimap-find-stl-clr.md)|尋找符合指定之索引鍵的項目。|  
|[multimap::insert](../dotnet/multimap-insert-stl-clr.md)|加入項目。|  
|[multimap::key\_comp](../dotnet/multimap-key-comp-stl-clr.md)|為兩個金鑰複製排序委派。|  
|[multimap::lower\_bound](../dotnet/multimap-lower-bound-stl-clr.md)|尋找符合指定索引鍵的範圍之開頭。|  
|[multimap::make\_value](../dotnet/multimap-make-value-stl-clr.md)|建構一個值物件。|  
|[multimap::multimap](../dotnet/multimap-multimap-stl-clr.md)|建構一個容器物件。|  
|[multimap::rbegin](../dotnet/multimap-rbegin-stl-clr.md)|指定已還原的受控制序列開頭。|  
|[multimap::rend](../dotnet/multimap-rend-stl-clr.md)|指定已還原的受控制序列結尾。|  
|[multimap::size](../dotnet/multimap-size-stl-clr.md)|計數項目的數目。|  
|[multimap::swap](../dotnet/multimap-swap-stl-clr.md)|交換兩個容器的內容。|  
|[multimap::to\_array](../dotnet/multimap-to-array-stl-clr.md)|複製受控制序列至新陣列。|  
|[multimap::upper\_bound](../dotnet/multimap-upper-bound-stl-clr.md)|尋找符合指定索引鍵的範圍之結尾。|  
|[multimap::value\_comp](../dotnet/multimap-value-comp-stl-clr.md)|複製兩個項目值的排序委派。|  
  
|運算子|說明|  
|---------|--------|  
|[multimap::operator\=](../dotnet/multimap-operator-assign-stl-clr.md)|取代受控制序列。|  
|[operator\!\= \(multimap\)](../dotnet/operator-inequality-multimap-stl-clr.md)|判斷 `multimap` 物件是否不等於另一個 `multimap` 物件。|  
|[operator\< \(multimap\)](../dotnet/operator-less-than-multimap-stl-clr.md)|判斷 `multimap` 物件是否小於另一個 `multimap` 物件。|  
|[operator\<\= \(multimap\)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)|判斷 `multimap` 物件是否小於或等於另外一個 `multimap` 物件。|  
|[operator\=\= \(multimap\)](../dotnet/operator-equality-multimap-stl-lr.md)|判斷 `multimap` 物件是否等於另一個 `multimap` 物件。|  
|[operator\> \(multimap\)](../dotnet/operator-greater-than-multimap-stl-clr.md)|判斷 `multimap` 物件是否大於另一個 `multimap` 物件。|  
|[operator\>\= \(multimap\)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)|判斷 `multimap` 物件是否大於或等於另外一個 `multimap` 物件。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.ICloneable>|複製物件。|  
|<xref:System.Collections.IEnumerable>|序列傳遞項目。|  
|<xref:System.Collections.ICollection>|維護項目的群組。|  
|<xref:System.Collections.Generic.IEnumerable%601>|序列傳遞型別項目。|  
|<xref:System.Collections.Generic.ICollection%601>|維護型別項目的群組。|  
|ITree\<Key, Value\>|維護泛型容器。|  
  
## 備註  
 物件配置和釋放其控制的序列之記憶體區域，如同個別的節點。  它會將項目插入 \(幾乎\) 平衡的樹狀結構，以修改節點之間的連結 \(而非複製節點的內容至另一個節點\) 來保持排序。  這表示您可以自由地插入和移除項目，而不會干擾其他項目。  
  
 它會藉由呼叫 [multimap::key\_compare](../dotnet/multimap-key-compare-stl-clr.md) 型別的儲存的委派物件，來控制物件的排序序列。  您可以在建構多點對應時指定儲存的委派物件；如果您不指定委派物件，預設為比較 `operator<(key_type, key_type)`。  您可以呼叫成員函式 `()`[multimap::key\_comp](../dotnet/multimap-key-comp-stl-clr.md) 存取這個儲存的物件。  
  
 這類委派物件必須實行嚴格弱式順序在 [multimap::key\_type](../dotnet/multimap-key-type-stl-clr.md) 型別的索引鍵上。  這表示，對於任何兩個索引鍵的 `X` 和 `Y`：  
  
 `key_comp()(X, Y)` 會在每次呼叫時傳回相同的布林值結果。  
  
 如果 `key_comp()(X, Y)` 為 true，則 `key_comp()(Y, X)` 必須為 false。  
  
 如果 `key_comp()(X, Y)` 為 true，則 `X` 會在 `Y` 之前排序。  
  
 如果 `!key_comp()(X, Y) && !key_comp()(Y, X)` 為 true，則 `X` 和 `Y` 會有相等排序。  
  
 對於在受控制序列中任何在 `Y` 之前的項目 `X`， `key_comp()(Y, X)` 會是 false。\(預設委派物件的金鑰值永遠不會減少。\)不同於樣板類別 [map](../dotnet/map-stl-clr.md)，樣板類別 `multimap` 的物件不需要所有項目的索引鍵都是唯一的。\(兩個以上的索引鍵可能有相等的排序。\)  
  
 每個項目包含個別的索引鍵和對應的值。  序列顯示的方式允許以和序列中 \(對數時間\) 項目數的對數成比例的作業數目，進行搜尋、插入和移除一個任意的項目。  而且，插入項目不會使迭代器失效，而移除項目只會使指向移除項目的迭代器失效。  
  
 多點對應支援雙向迭代器，這表示您可以逐步執行至指定的迭代器在受控制序列中指定的相鄰項目。  特殊前端節點對應於 [multimap::end](../dotnet/multimap-end-stl-clr.md)`()` 所傳回的迭代器。  如果存在，您可以這個迭代器到達受控制序列的最後一個項目。  您可以增加多點對應迭代器以到達前端節點，然後它會與 `end()` 比較是否相等。  但是，您無法對 `end()` 傳回的迭代器取值。  
  
 請注意您無法直接以數值位置參考指定的多點對應元素，這需要一個隨機存取迭代器。  
  
 多點對應迭代器會儲存控制代碼至關聯的多點對應節點，其會接著儲存控制代碼至關聯的容器。  您只能將迭代器與其關聯的容器物件一起使用。  只要其關聯的多點對應節點與某一多點對應相關聯，則多點對應迭代器會保持有效。  而且，有效迭代器是可取值的，您可以使用它存取或替換它指派的值，只要不等於 `end()`。  
  
 清除或移除元素會呼叫它的儲存值的解構函式。  終結容器清除所有項目。  因此，項目型別是 ref 類別的容器會確保沒有項目的存在時間比容器久。  然而，請注意控制碼的容器使用 `not` 終結其項目。  
  
## 需求  
 **標頭：** \<cliext\/map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)