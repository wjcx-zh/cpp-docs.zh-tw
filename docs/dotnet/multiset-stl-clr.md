---
title: "multiset (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/set> 標頭 [STL/CLR]"
  - "<set> 標頭 [STL/CLR]"
  - "multiset 類別 [STL/CLR]"
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述一個物件，其控制一個可雙向存取項目的變更長度序列。  您使用容器 `multiset` 處理項目序列，做為 \(幾乎\) 平衡且排序的樹，其每個節點儲存一個項目。  
  
 在如下解譯， `GValue` 與 `GKey`，而 `Key` 相同，除非後面是參考型別，在這種情況下，它是 `Key^`的情況下。  
  
## 語法  
  
```  
template<typename Key>  
    ref class multiset  
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
  
## 成員  
  
|型別定義|說明|  
|----------|--------|  
|[multiset::const\_iterator](../dotnet/multiset-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[multiset::const\_reference](../dotnet/multiset-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[multiset::const\_reverse\_iterator](../dotnet/multiset-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器型別。|  
|[multiset::difference\_type](../dotnet/multiset-difference-type-stl-clr.md)|兩個項目之間的 \(可能帶正負號\) 距離的型別。|  
|[multiset::generic\_container](../dotnet/multiset-generic-container-stl-clr.md)|容器的泛型介面的型別。|  
|[multiset::generic\_iterator](../dotnet/multiset-generic-iterator-stl-clr.md)|容器的泛型介面的迭代器的型別。|  
|[multiset::generic\_reverse\_iterator](../dotnet/multiset-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器的型別。|  
|[multiset::generic\_value](../dotnet/multiset-generic-value-stl-clr.md)|容器的泛型介面的元素的型別。|  
|[multiset::iterator](../dotnet/multiset-iterator-stl-clr.md)|受控制序列中 iterator 的類型。|  
|[multiset::key\_compare](../dotnet/multiset-key-compare-stl-clr.md)|兩個金鑰的排序委派。|  
|[multiset::key\_type](../dotnet/multiset-key-type-stl-clr.md)|排序索引鍵的類型。|  
|[multiset::reference](../dotnet/multiset-reference-stl-clr.md)|項目的參考類型。|  
|[multiset::reverse\_iterator](../dotnet/multiset-reverse-iterator-stl-clr.md)|用於受控制序列的反向迭代器型別。|  
|[multiset::size\_type](../dotnet/multiset-size-type-stl-clr.md)|兩個項目之間的 \(非負數\) 距離的型別。|  
|[multiset::value\_compare](../dotnet/multiset-value-compare-stl-clr.md)|兩個項目值的排序委派。|  
|[multiset::value\_type](../dotnet/multiset-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[multiset::begin](../dotnet/multiset-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[multiset::clear](../dotnet/multiset-clear-stl-clr.md)|移除所有項目。|  
|[multiset::count](../dotnet/multiset-count-stl-clr.md)|計算符合指定索引鍵的項目。|  
|[multiset::empty](../dotnet/multiset-empty-stl-clr.md)|測試是否不存在項目。|  
|[multiset::end](../dotnet/multiset-end-stl-clr.md)|指定受控制序列的結尾。|  
|[multiset::equal\_range](../dotnet/multiset-equal-range-stl-clr.md)|尋找符合指定索引鍵的範圍。|  
|[multiset::erase](../dotnet/multiset-erase-stl-clr.md)|移除指定位置的項目。|  
|[multiset::find](../dotnet/multiset-find-stl-clr.md)|尋找符合指定之索引鍵的項目。|  
|[multiset::insert](../dotnet/multiset-insert-stl-clr.md)|加入項目。|  
|[multiset::key\_comp](../dotnet/multiset-key-comp-stl-clr.md)|為兩個金鑰複製排序委派。|  
|[multiset::lower\_bound](../dotnet/multiset-lower-bound-stl-clr.md)|尋找符合指定索引鍵的範圍之開頭。|  
|[multiset::make\_value](../dotnet/multiset-make-value-stl-clr.md)|建構一個值物件。|  
|[multiset::multiset](../dotnet/multiset-multiset-stl-clr.md)|建構一個容器物件。|  
|[multiset::rbegin](../dotnet/multiset-rbegin-stl-clr.md)|指定已還原的受控制序列開頭。|  
|[multiset::rend](../dotnet/multiset-rend-stl-clr.md)|指定已還原的受控制序列結尾。|  
|[multiset::size](../dotnet/multiset-size-stl-clr.md)|計數項目的數目。|  
|[multiset::swap](../dotnet/multiset-swap-stl-clr.md)|交換兩個容器的內容。|  
|[multiset::to\_array](../dotnet/multiset-to-array-stl-clr.md)|複製受控制序列至新陣列。|  
|[multiset::upper\_bound](../dotnet/multiset-upper-bound-stl-clr.md)|尋找符合指定索引鍵的範圍之結尾。|  
|[multiset::value\_comp](../dotnet/multiset-value-comp-stl-clr.md)|複製兩個項目值的排序委派。|  
  
|運算子|說明|  
|---------|--------|  
|[multiset::operator\=](../dotnet/multiset-operator-assign-stl-clr.md)|取代受控制序列。|  
|[operator\!\= \(multiset\)](../dotnet/operator-inequality-multiset-stl-clr.md)|判斷 `multiset` 物件是否不等於另一個 `multiset` 物件。|  
|[operator\< \(multiset\)](../dotnet/operator-less-than-multiset-stl-clr.md)|判斷 `multiset` 物件是否小於另一個 `multiset` 物件。|  
|[operator\<\= \(multiset\)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)|判斷 `multiset` 物件是否小於或等於另外一個 `multiset` 物件。|  
|[operator\=\= \(multiset\)](../dotnet/operator-equality-multiset-stl-clr.md)|判斷 `multiset` 物件是否等於另一個 `multiset` 物件。|  
|[operator\> \(multiset\)](../dotnet/operator-greater-than-multiset-stl-clr.md)|判斷 `multiset` 物件是否大於另一個 `multiset` 物件。|  
|[operator\>\= \(multiset\)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)|判斷 `multiset` 物件是否大於或等於另外一個 `multiset` 物件。|  
  
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
  
 它會藉由呼叫 [multiset::key\_compare](../dotnet/multiset-key-compare-stl-clr.md)型別所儲存的委派物件控制物件的排序序列。  您可以在建構多點集合時指定儲存的委派物件；如果您不指定委派物件，預設為比較 `operator<(key_type, key_type)`。  您可以呼叫成員函式存取這個儲存物件的`()`[multiset::key\_comp](../dotnet/multiset-key-comp-stl-clr.md)。  
  
 這類委派物件必須實行嚴格弱式順序在 [multiset::key\_type](../dotnet/multiset-key-type-stl-clr.md) 型別的索引鍵上。  這表示，對於任何兩個索引鍵的 `X` 和 `Y`：  
  
 `key_comp()(X, Y)` 會在每次呼叫時傳回相同的布林值結果。  
  
 如果 `key_comp()(X, Y)` 為 true，則 `key_comp()(Y, X)` 必須為 false。  
  
 如果 `key_comp()(X, Y)` 為 true，則 `X` 會在 `Y` 之前排序。  
  
 如果 `!key_comp()(X, Y) && !key_comp()(Y, X)` 為 true，則 `X` 和 `Y` 會有相等排序。  
  
 對於在受控制序列中任何在 `Y` 之前的項目 `X`， `key_comp()(Y, X)` 會是 false。\(預設委派物件的金鑰值永遠不會減少。\)不同於樣板類別 [set](../dotnet/set-stl-clr.md)，樣板類別 `multiset` 物件不需要所有項目的索引鍵是唯一的。\(兩個以上的索引鍵可能有相等的排序。\)  
  
 每個項目做為索引鍵和值。  序列顯示的方式允許以和序列中 \(對數時間\) 項目數的對數成比例的作業數目，進行搜尋、插入和移除一個任意的項目。  而且，插入項目不會使迭代器失效，而移除項目只會使指向移除項目的迭代器失效。  
  
 多點集合支援雙向迭代器，這表示您可以逐步執行至指定的迭代器在受控制序列中指定的相鄰項目。  特殊前端節點對應於 [multiset::end](../dotnet/multiset-end-stl-clr.md)所傳回的 Iterator`()`。  如果存在，您可以這個迭代器到達受控制序列的最後一個項目。  您可以增加多點集合迭代器以到達前端節點，然後它會與 `end()` 比較是否相等。  但是，您無法對 `end()` 傳回的迭代器取值。  
  
 請注意您無法直接以數值位置參考指定的多點集合元素，這需要一個隨機存取迭代器。  
  
 多點集合會儲存控制代碼至關聯的多點集合節點，其會接著儲存控制代碼至關聯的容器。  您只能將迭代器與其關聯的容器物件一起使用。  只要其關聯的多點集合節點與某一多點集合相關聯，則多點集合迭代器會保持有效。  而且，有效迭代器是可取值的，您可以使用它存取或替換它指派的值，只要不等於 `end()`。  
  
 清除或移除元素會呼叫它的儲存值的解構函式。  終結容器清除所有項目。  因此，項目型別是 ref 類別的容器會確保沒有項目的存在時間比容器久。  然而，請注意控制碼的容器使用 `not` 終結其項目。  
  
## 需求  
 **標頭：** \<cliext\/set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)