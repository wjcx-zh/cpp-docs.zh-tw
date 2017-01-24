---
title: "map (STL/CLR) | Microsoft Docs"
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
  - "cliext::map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/map> 標頭 [STL/CLR]"
  - "<map> 標頭 [STL/CLR]"
  - "map 類別 [STL/CLR]"
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述物件控制存取雙向項目的變更長度序列。  您使用容器 `map` 處理項目序列做為 \(幾乎\) 之間平衡樹狀節點已排序，則每個儲存的項目。  包含項目的索引鍵，排序的序列和對應的值，為乘巡移至。  
  
 在如下解譯， `GValue` 相同如下:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey` 與 `Key` ，除非後面是參考型別，在這種情況下，它是 `Key^`的情況下  
  
 `GMapped` 與 `Mapped` ，除非後面是參考型別，在這種情況下，它是 `Mapped^`的情況下  
  
## 語法  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
#### 參數  
 Key  
 受控制序列中項目的主要元件型別。  
  
 已對應  
 受控制序列中項目的額外元件型別。  
  
## 成員  
  
|類型定義|說明|  
|----------|--------|  
|[map::const\_iterator](../dotnet/map-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[map::const\_reference](../dotnet/map-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[map::const\_reverse\_iterator](../dotnet/map-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[map::difference\_type](../dotnet/map-difference-type-stl-clr.md)|兩個項目之間的\(可能帶正負號\)距離的類型。|  
|[map::generic\_container](../dotnet/map-generic-container-stl-clr.md)|泛型介面的型別的容器。|  
|[map::generic\_iterator](../dotnet/map-generic-iterator-stl-clr.md)|容器的泛型介面的迭代器的型別。|  
|[map::generic\_reverse\_iterator](../dotnet/map-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器的型別。|  
|[map::generic\_value](../dotnet/map-generic-value-stl-clr.md)|容器的泛型介面的元素的型別。|  
|[map::iterator](../dotnet/map-iterator-stl-clr.md)|受控制序列中 iterator 的類型。|  
|[map::key\_compare](../dotnet/map-key-compare-stl-clr.md)|兩個金鑰的排序委派。|  
|[map::key\_type](../dotnet/map-key-type-stl-clr.md)|排序索引鍵的類型。|  
|[map::mapped\_type](../dotnet/map-mapped-type-stl-clr.md)|與每個索引鍵關聯的對應值類型。|  
|[map::reference](../dotnet/map-reference-stl-clr.md)|項目的參考類型。|  
|[map::reverse\_iterator](../dotnet/map-reverse-iterator-stl-clr.md)|用於受控制序列的反向迭代器類型。|  
|[map::size\_type](../dotnet/map-size-type-stl-clr.md)|兩個項目之間的\(非負號\)距離的類型。|  
|[map::value\_compare](../dotnet/map-value-compare-stl-clr.md)|兩個項目值的排序委派。|  
|[map::value\_type](../dotnet/map-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[map::begin](../dotnet/map-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[map::clear](../dotnet/map-clear-stl-clr.md)|移除所有項目。|  
|[map::count](../dotnet/map-count-stl-clr.md)|計算符合指定索引鍵的項目。|  
|[map::empty](../dotnet/map-empty-stl-clr.md)|測試項目是否不存在。|  
|[map::end](../dotnet/map-end-stl-clr.md)|指定受控制序列的結尾。|  
|[map::equal\_range](../dotnet/map-equal-range-stl-clr.md)|尋找符合指定索引鍵的範圍。|  
|[map::erase](../dotnet/map-erase-stl-clr.md)|移除指定位置的項目。|  
|[map::find](../dotnet/map-find-stl-clr.md)|尋找符合指定之索引鍵的項目。|  
|[map::insert](../dotnet/map-insert-stl-clr.md)|加入項目。|  
|[map::key\_comp](../dotnet/map-key-comp-stl-clr.md)|複製兩個金鑰的排序委派。|  
|[map::lower\_bound](../dotnet/map-lower-bound-stl-clr.md)|尋找符合指定索引鍵的項目範圍的開頭。|  
|[map::make\_value](../dotnet/map-make-value-stl-clr.md)|建構一個值物件。|  
|[map::map](../dotnet/map-map-stl-clr.md)|建構一個容器物件。|  
|[map::rbegin](../dotnet/map-rbegin-stl-clr.md)|指定已還原的受控制序列開頭。|  
|[map::rend](../dotnet/map-rend-stl-clr.md)|指定已還原的受控制序列結尾。|  
|[map::size](../dotnet/map-size-stl-clr.md)|計數項目的數目。|  
|[map::swap](../dotnet/map-swap-stl-clr.md)|交換兩個容器的內容。|  
|[map::to\_array](../dotnet/map-to-array-stl-clr.md)|複製受控制序列到新陣列。|  
|[map::upper\_bound](../dotnet/map-upper-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍結尾。|  
|[map::value\_comp](../dotnet/map-value-comp-stl-clr.md)|複製兩個項目值的排序委派。|  
  
|運算子|說明|  
|---------|--------|  
|[map::operator\=](../dotnet/map-operator-assign-stl-clr.md)|取代受控制序列。|  
|[map::operator](../dotnet/map-operator-stl-clr.md)|將索引鍵對應至其關聯的對應值。|  
|[operator\!\= \(map\)](../dotnet/operator-inequality-map-stl-clr.md)|判斷 `map` 物件是否不等於另一個 `map` 物件。|  
|[operator\< \(map\)](../dotnet/operator-less-than-map-stl-clr.md)|判斷 `map` 物件是否小於另一個 `map` 物件。|  
|[operator\<\= \(map\)](../dotnet/operator-less-or-equal-map-stl-clr.md)|判斷 `map` 物件是否小於或等於另外一個 `map` 物件。|  
|[operator\=\= \(map\)](../dotnet/operator-equality-map-stl-clr.md)|判斷 `map` 物件是否等於另一個 `map` 物件。|  
|[operator\> \(map\)](../dotnet/operator-greater-than-map-stl-clr.md)|判斷 `map` 物件是否大於另一個 `map` 物件。|  
|[operator\>\= \(map\)](../dotnet/operator-greater-or-equal-map-stl-clr.md)|判斷 `map` 物件是否大於或等於另外一個 `map` 物件。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.ICloneable>|重複物件。|  
|<xref:System.Collections.IEnumerable>|序列傳遞項目。|  
|<xref:System.Collections.ICollection>|維護項目的群組。|  
|<xref:System.Collections.Generic.IEnumerable%601>|序列傳遞型別項目。|  
|<xref:System.Collections.Generic.ICollection%601>|維護型別項目的群組。|  
|<xref:System.Collections.Generic.IDictionary%602>|維護{0}索引鍵，其值為的群組。|  
|ITreeKey\<關鍵值\>|維護泛型容器。|  
  
## 備註  
 物件配置和未使用的記憶體區域的控制項會以個別節點的序列。  它會將項目插入其保持排序修改節點之間的連結 \(幾乎\) 平衡樹狀結構，您可以將節點的內容至另一個。  這表示您可以自由地插入和移除項目，而不會干擾其他項目。  
  
 它會藉由呼叫 [map::key\_compare](../dotnet/map-key-compare-stl-clr.md)型別所儲存的委派物件控制物件的排序序列。  在建構對應時，您可以指定儲存委派物件;如果您不指定委派物件，預設為比較 `operator<(key_type, key_type)`。  您可以呼叫成員函式存取這個儲存物件的`()`[map::key\_comp](../dotnet/map-key-comp-stl-clr.md)。  
  
 這類委派物件必須強制嚴格弱式順序給 [map::key\_type](../dotnet/map-key-type-stl-clr.md)型別的索引鍵。  這表示，任何兩個索引鍵的 `X` 和 `Y`:  
  
 `key_comp()(X, Y)` 會在每次呼叫相同的布林值結果。  
  
 如果 `key_comp()(X, Y)` 為 true，則 `key_comp()(Y, X)` 必須為 false。  
  
 如果 `key_comp()(X, Y)` 為 true，則 `X` 會在 `Y`之前。  
  
 如果 `!key_comp()(X, Y) && !key_comp()(Y, X)` 為 true，則 `X` 和 `Y` 有相同 Bucket 的項目。  
  
 對於在受控制序列的 `Y` 之前的任何項目則為 `X` ， `key_comp()(Y, X)` 是錯誤的。\(預設委派物件，金鑰會減少值\)。不同於樣板類別 [map](../dotnet/map-stl-clr.md)，樣板類別 `map` 物件不需要所有項目的索引鍵是唯一的。\(兩個以上按鍵可能相同 Bucket 的項目\)。  
  
 每個項目都包含個別的索引鍵和對應的值。  序列表示允許搜尋、一個選擇性項目插入和移除與許多作業的比例與項目數目之值序列中的方法 \(\) 時間\)。  而且，插入項目不無效 Iterator，，並移除項目無法使用點所移除的項目僅 Iterator。  
  
 對應支援雙向 Iterator，這表示您可以逐步執行至指定的相鄰項目的 Iterator 在受控制序列的項目。  特殊前端節點對應於 [map::end](../dotnet/map-end-stl-clr.md)所傳回的 Iterator`()`。  如果您以這個 Iterator 到達受控制序列的最後一個項目。  您可以將對應 Iterator 到達前端節點，因此，它與 `end()`會比較相等。  但是，您無法取值 `end()`所傳回的 Iterator。  
  
 請注意您無法直接參考指定的對應元素其數值位置\-\-該要求隨機存取 Iterator。  
  
 對應中儲存的控制代碼關聯的網站導覽節點，接著儲存的控制代碼關聯的容器。  您只能使用 Iterator 與其關聯的容器物件。  只要其關聯的導覽節點與某一對應，對應 Iterator 保持有效。  而且，有效 Iterator dereferencable\-\-您可以使用它所指派它存取或修改項目的值\-\-只要不等於 `end()`。  
  
 清除或移除元素呼叫它的儲存值的解構函式。  終結容器清除所有項目。  因此，項目型別是 ref 類別的容器確保項目不使用得比容器的。  請注意，然而，容器控制碼做 `not` 終結的項目。  
  
## 需求  
 **標頭：** \<cliext\/map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)