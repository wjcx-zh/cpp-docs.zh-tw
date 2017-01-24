---
title: "hash_map (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/hash_map> 標頭 [STL/CLR]"
  - "<hash_map> 標頭 [STL/CLR]"
  - "hash_map 類別 [STL/CLR]"
ms.assetid: c3cfc69b-04c6-42ae-a30e-0eda953fe883
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述物件控制存取雙向項目的變更長度序列。  您使用容器 `hash_map` 處理項目序列做為雜湊資料表，每個清單項目儲存節點的雙向連結串列和儲存項目的每個節點。  包含項目的索引鍵，排序的序列和對應的值，為乘巡移至。  
  
 在如下解譯， `GValue` 相同如下:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey` 與 `Key` ，除非後面是參考型別，在這種情況下，它是 `Key^`的情況下  
  
 `GMapped` 與 `Mapped` ，除非後面是參考型別，在這種情況下，它是 `Mapped^`的情況下  
  
## 語法  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class hash_map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
    { ..... };  
```  
  
#### 參數  
 Key  
 受控制序列中項目的主要元件型別。  
  
 對應  
 項目的其他元件型別指定受控制序列。  
  
## 成員  
  
|型別定義|說明|  
|----------|--------|  
|[hash\_map::const\_iterator](../dotnet/hash-map-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[hash\_map::const\_reference](../dotnet/hash-map-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[hash\_map::const\_reverse\_iterator](../dotnet/hash-map-const-reverse-iterator-stl-clr.md)|常數反向 Iterator 的型別受控制序列的。|  
|[hash\_map::difference\_type](../dotnet/hash-map-difference-type-stl-clr.md)|\(可能簽署\) 距離的型別有兩個項目之間的間距。|  
|[hash\_map::generic\_container](../dotnet/hash-map-generic-container-stl-clr.md)|泛型介面的型別的容器。|  
|[hash\_map::generic\_iterator](../dotnet/hash-map-generic-iterator-stl-clr.md)|Iterator 的型別泛型介面的容器。|  
|[hash\_map::generic\_reverse\_iterator](../dotnet/hash-map-generic-reverse-iterator-stl-clr.md)|反向 Iterator 的型別泛型介面的容器。|  
|[hash\_map::generic\_value](../dotnet/hash-map-generic-value-stl-clr.md)|項目的型別泛型介面的容器。|  
|[hash\_map::hasher](../dotnet/hash-map-hasher-stl-clr.md)|索引鍵的雜湊委派。|  
|[hash\_map::iterator](../dotnet/hash-map-iterator-stl-clr.md)|受控制序列中 iterator 的類型。|  
|[hash\_map::key\_compare](../dotnet/hash-map-key-compare-stl-clr.md)|兩個索引鍵的順序委派。|  
|[hash\_map::key\_type](../dotnet/hash-map-key-type-stl-clr.md)|排序索引鍵的類型。|  
|[hash\_map::mapped\_type](../dotnet/hash-map-mapped-type-stl-clr.md)|對應值的型別與每個索引鍵。|  
|[hash\_map::reference](../dotnet/hash-map-reference-stl-clr.md)|項目的參考類型。|  
|[hash\_map::reverse\_iterator](../dotnet/hash-map-reverse-iterator-stl-clr.md)|反向 Iterator 的型別受控制序列的。|  
|[hash\_map::size\_type](../dotnet/hash-map-size-type-stl-clr.md)|\(非負數\) 距離的型別有兩個項目之間的間距。|  
|[hash\_map::value\_compare](../dotnet/hash-map-value-compare-stl-clr.md)|兩個項目值的排序委派。|  
|[hash\_map::value\_type](../dotnet/hash-map-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[hash\_map::begin](../dotnet/hash-map-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[hash\_map::bucket\_count](../dotnet/hash-map-bucket-count-stl-clr.md)|計數 Bucket 的數目。|  
|[hash\_map::clear](../dotnet/hash-map-clear-stl-clr.md)|移除所有項目。|  
|[hash\_map::count](../dotnet/hash-map-count-stl-clr.md)|計算符合指定索引鍵的項目。|  
|[hash\_map::empty](../dotnet/hash-map-empty-stl-clr.md)|測試項目是否不存在。|  
|[hash\_map::end](../dotnet/hash-map-end-stl-clr.md)|指定受控制序列的結尾。|  
|[hash\_map::equal\_range](../dotnet/hash-map-equal-range-stl-clr.md)|尋找符合指定索引鍵的範圍。|  
|[hash\_map::erase](../dotnet/hash-map-erase-stl-clr.md)|移除指定位置的項目。|  
|[hash\_map::find](../dotnet/hash-map-find-stl-clr.md)|尋找符合指定之索引鍵的項目。|  
|[hash\_map::hash\_delegate](../dotnet/hash-map-hash-delegate-stl-clr.md)|複製索引鍵的雜湊委派。|  
|[hash\_map::hash\_map](../dotnet/hash-map-hash-map-stl-clr.md)|建構一個容器物件。|  
|[hash\_map::insert](../dotnet/hash-map-insert-stl-clr.md)|加入項目。|  
|[hash\_map::key\_comp](../dotnet/hash-map-key-comp-stl-clr.md)|複製兩個索引鍵的順序委派。|  
|[hash\_map::load\_factor](../dotnet/hash-map-load-factor-stl-clr.md)|計數平均項目每個 Bucket。|  
|[hash\_map::lower\_bound](../dotnet/hash-map-lower-bound-stl-clr.md)|尋找符合指定索引鍵的項目範圍的開頭。|  
|[hash\_map::make\_value](../dotnet/hash-map-make-value-stl-clr.md)|建構值物件。|  
|[hash\_map::max\_load\_factor](../dotnet/hash-map-max-load-factor-stl-clr.md)|取得或設定最大元素每個 Bucket。|  
|[hash\_map::rbegin](../dotnet/hash-map-rbegin-stl-clr.md)|指定已還原的受控制序列開頭。|  
|[hash\_map::rehash](../dotnet/hash-map-rehash-stl-clr.md)|重新建置雜湊資料表。|  
|[hash\_map::rend](../dotnet/hash-map-rend-stl-clr.md)|指定已還原的受控制序列結尾。|  
|[hash\_map::size](../dotnet/hash-map-size-stl-clr.md)|計數項目的數目。|  
|[hash\_map::swap](../dotnet/hash-map-swap-stl-clr.md)|交換兩個容器的內容。|  
|[hash\_map::to\_array](../dotnet/hash-map-to-array-stl-clr.md)|複製受控制序列的新陣列。|  
|[hash\_map::upper\_bound](../dotnet/hash-map-upper-bound-stl-clr.md)|符合指定之索引鍵的範圍中尋找結尾。|  
|[hash\_map::value\_comp](../dotnet/hash-map-value-comp-stl-clr.md)|複製兩個項目值的排序委派。|  
  
|運算子|說明|  
|---------|--------|  
|[hash\_map::operator\=](../dotnet/hash-map-operator-assign-stl-clr.md)|取代受控制序列。|  
|[hash\_map::operator](../dotnet/hash-map-operator-stl-clr.md)|將索引鍵對應至其關聯的對應值。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.ICloneable>|複製物件。|  
|<xref:System.Collections.IEnumerable>|序列傳遞項目。|  
|<xref:System.Collections.ICollection>|維護項目的群組。|  
|<xref:System.Collections.Generic.IEnumerable%601>|序列傳遞型別項目。|  
|<xref:System.Collections.Generic.ICollection%601>|維護型別項目的群組。|  
|<xref:System.Collections.Generic.IDictionary%602>|維護{0}索引鍵，其值為的群組。|  
|IHashKey\<，值\>|維護泛型容器。|  
  
## 備註  
 物件配置和未使用的記憶體區域的控制項會以個別節點在雙向連結串列的序列。  若要快速存取，物件也會維護指標輸入清單 \(雜湊資料表\)，有效地處理整個清單做為子序列或 Bucket 的變更長度陣列。  它會將項目插入其保持排序修改節點之間的連結的 Bucket，藉由複製的節點內容到另一個。  這表示您可以自由地插入和移除項目，而不會干擾其他項目。  
  
 它會藉由呼叫 [hash\_set::key\_compare](../dotnet/hash-set-key-compare-stl-clr.md)型別所儲存的委派物件控制項的物件排序每個 Bucket。  在建構 hash\_set 時，您可以指定儲存委派物件;如果您不指定委派物件，預設為比較 `operator<=(key_type, key_type)`。  
  
 您可以呼叫成員函式存取所儲存委派物件 [hash\_set::key\_comp](../dotnet/hash-set-key-comp-stl-clr.md)`()`。  這類委派物件必須定義型別之間 [hash\_set::key\_type](../dotnet/hash-set-key-type-stl-clr.md)索引鍵的相等排序。  這表示，任何兩個索引鍵的 `X` 和 `Y`:  
  
 `key_comp()(X, Y)` 會在每次呼叫相同的布林值結果。  
  
 如果 `key_comp()(X, Y) && key_comp()(Y, X)` 為 true，則 `X` 和 `Y` 有相同 Bucket 的項目。  
  
 的行為與 `operator<=(key_type, key_type)`、 `operator>=(key_type, key_type)` 或 `operator==(key_type, key_type)` 所定義 eqivalent 定序的任何排序規則。  
  
 請注意容器確保只有索引鍵有相等排序的項目，而 \(雜湊為相同的整數值\) 在 Bucket 中相鄰的。  不同於樣板類別 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)，樣板類別 `hash_map` 物件可確保所有項目的索引鍵是唯一的。\(這兩個金鑰不相等排序\)。  
  
 物件會判斷哪一個 Bucket 中也應該呼叫 [hash\_set::hasher](../dotnet/hash-set-hasher-stl-clr.md)型別所儲存的委派物件包含指定的排序索引鍵。  您可以呼叫成員函式 [hash\_set::hash\_delegate](../dotnet/hash-set-hash-delegate-stl-clr.md)`()` 取得取決於這個機碼值的整數值來存取這個中的物件。  在建構 hash\_set 時，您可以指定儲存委派物件;如果您不指定委派物件，預設是 `System::Object::hash_value(key_type)`函式。  這表示，任何索引鍵的 `X` 和 `Y`:  
  
 `hash_delegate()(X)` 會在每個呼叫的同一個整數結果。  
  
 如果 `X` 與 `Y` 相同 Bucket 的項目，則 `hash_delegate()(X)` 會傳回整數結果與 `hash_delegate()(Y)`相同。  
  
 每個項目都包含個別的索引鍵和對應的值。  序列表示允許搜尋、一個選擇性項目插入和移除與許多作業的是項目數目獨立序列中的方法 \(常數時間\)\-\-至少在情況下最好。  而且，插入項目不無效 Iterator，，並移除項目無法使用點所移除的項目僅 Iterator。  
  
 如果雜湊值不一致地散發，然而，雜湊資料表可能降低。  非常\-\-對於永遠都會傳回相同值的雜湊函式。\-\-搜尋、插入和移除與項目數目成正比順序 \(線性時間\)。  容器竭力選取合理的雜湊函式、印表機 Bucket 大小和 Hashtable 大小 \(Bucket 總數\)，不過，您可以覆寫任一或全部的索引。  請參閱，例如， [hash\_set::max\_load\_factor](../dotnet/hash-set-max-load-factor-stl-clr.md) 和 [hash\_set::rehash](../dotnet/hash-set-rehash-stl-clr.md)函式。  
  
 hash\_map 支援雙向 Iterator，這表示您可以逐步執行至指定的相鄰項目的 Iterator 在受控制序列的項目。  特殊前端節點對應於 [hash\_map::end](../dotnet/hash-map-end-stl-clr.md)所傳回的 Iterator`()`。  如果您以這個 Iterator 到達受控制序列的最後一個項目。  您可以將 hash\_map Iterator 到達前端節點，因此，它與 `end()`會比較相等。  但是，您無法取值 `end()`所傳回的 Iterator。  
  
 請注意您無法直接參考指定的 hash\_map 項目其數值位置\-\-該要求隨機存取 Iterator。  
  
 hash\_map Iterator 儲存控制代碼關聯的 hash\_map 節點，接著儲存的控制代碼關聯的容器。  您只能使用 Iterator 與其關聯的容器物件。  只要其相關 hash\_map 節點與一些 hash\_map， hash\_map Iterator 保持有效。  而且，有效 Iterator dereferencable\-\-您可以使用它所指派它存取或修改項目的值\-\-只要不等於 `end()`。  
  
 清除或移除元素呼叫它的儲存值的解構函式。  終結容器清除所有項目。  因此，項目型別是 ref 類別的容器確保項目不使用得比容器的。  請注意，然而，容器控制碼做 `not` 終結的項目。  
  
## 需求  
 **標題:** \<cliext\/hash\_map\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)