---
title: "hash_multiset (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/hash_set> 標頭 [STL/CLR]"
  - "<hash_set> 標頭 [STL/CLR]"
  - "hash_multiset 類別 [STL/CLR]"
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述物件控制存取雙向項目的變更長度序列。  您使用容器 `hash_multiset` 處理項目序列做為雜湊資料表，每個清單項目儲存節點的雙向連結串列和儲存項目的每個節點。  每個項目的值做為索引鍵，用於排序序列。  
  
 在如下解譯， `GValue` 與 `GKey`，而 `Key` 相同，除非後面是參考型別，在這種情況下，它是 `Key^`的情況下。  
  
## 語法  
  
```  
template<typename Key>  
    ref class hash_multiset  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
    { ..... };  
```  
  
#### 參數  
 Key  
 受控制序列中項目的主要元件型別。  
  
## 成員  
  
|類型定義|說明|  
|----------|--------|  
|[hash\_multiset::const\_iterator](../dotnet/hash-multiset-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[hash\_multiset::const\_reference](../dotnet/hash-multiset-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[hash\_multiset::const\_reverse\_iterator](../dotnet/hash-multiset-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[hash\_multiset::difference\_type](../dotnet/hash-multiset-difference-type-stl-clr.md)|兩個項目之間的\(可能帶正負號\)距離的類型。|  
|[hash\_multiset::generic\_container](../dotnet/hash-multiset-generic-container-stl-clr.md)|泛型介面的型別的容器。|  
|[hash\_multiset::generic\_iterator](../dotnet/hash-multiset-generic-iterator-stl-clr.md)|容器的泛型介面的迭代器的型別。|  
|[hash\_multiset::generic\_reverse\_iterator](../dotnet/hash-multiset-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器的型別。|  
|[hash\_multiset::generic\_value](../dotnet/hash-multiset-generic-value-stl-clr.md)|容器的泛型介面的元素的型別。|  
|[hash\_multiset::hasher](../dotnet/hash-multiset-hasher-stl-clr.md)|索引鍵的雜湊委派。|  
|[hash\_multiset::iterator](../dotnet/hash-multiset-iterator-stl-clr.md)|受控制序列中 iterator 的類型。|  
|[hash\_multiset::key\_compare](../dotnet/hash-multiset-key-compare-stl-clr.md)|兩個金鑰的排序委派。|  
|[hash\_multiset::key\_type](../dotnet/hash-multiset-key-type-stl-clr.md)|排序索引鍵的類型。|  
|[hash\_multiset::reference](../dotnet/hash-multiset-reference-stl-clr.md)|項目的參考類型。|  
|[hash\_multiset::reverse\_iterator](../dotnet/hash-multiset-reverse-iterator-stl-clr.md)|用於受控制序列的反向迭代器類型。|  
|[hash\_multiset::size\_type](../dotnet/hash-multiset-size-type-stl-clr.md)|兩個項目之間的\(非負號\)距離的類型。|  
|[hash\_multiset::value\_compare](../dotnet/hash-multiset-value-compare-stl-clr.md)|兩個項目值的排序委派。|  
|[hash\_multiset::value\_type](../dotnet/hash-multiset-value-type-stl-clr.md)|項目的類型。|  
  
|成員函式|說明|  
|----------|--------|  
|[hash\_multiset::begin](../dotnet/hash-multiset-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[hash\_multiset::bucket\_count](../dotnet/hash-multiset-bucket-count-stl-clr.md)|計數 Bucket 的數目。|  
|[hash\_multiset::clear](../dotnet/hash-multiset-clear-stl-clr.md)|移除所有項目。|  
|[hash\_multiset::count](../dotnet/hash-multiset-count-stl-clr.md)|計算符合指定索引鍵的項目。|  
|[hash\_multiset::empty](../dotnet/hash-multiset-empty-stl-clr.md)|測試項目是否不存在。|  
|[hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)|指定受控制序列的結尾。|  
|[hash\_multiset::equal\_range](../dotnet/hash-multiset-equal-range-stl-clr.md)|尋找符合指定索引鍵的範圍。|  
|[hash\_multiset::erase](../dotnet/hash-multiset-erase-stl-clr.md)|移除指定位置的項目。|  
|[hash\_multiset::find](../dotnet/hash-multiset-find-stl-clr.md)|尋找符合指定之索引鍵的項目。|  
|[hash\_multiset::hash\_delegate](../dotnet/hash-multiset-hash-delegate-stl-clr.md)|複製索引鍵的雜湊委派。|  
|[hash\_multiset::hash\_multiset](../dotnet/hash-multiset-hash-multiset-stl-clr.md)|建構一個容器物件。|  
|[hash\_multiset::insert](../dotnet/hash-multiset-insert-stl-clr.md)|加入項目。|  
|[hash\_multiset::key\_comp](../dotnet/hash-multiset-key-comp-stl-clr.md)|複製兩個金鑰的排序委派。|  
|[hash\_multiset::load\_factor](../dotnet/hash-multiset-load-factor-stl-clr.md)|計數平均項目每個 Bucket。|  
|[hash\_multiset::lower\_bound](../dotnet/hash-multiset-lower-bound-stl-clr.md)|尋找符合指定索引鍵的項目範圍的開頭。|  
|[hash\_multiset::make\_value](../dotnet/hash-multiset-make-value-stl-clr.md)|建構一個值物件。|  
|[hash\_multiset::max\_load\_factor](../dotnet/hash-multiset-max-load-factor-stl-clr.md)|取得或設定最大元素每個 Bucket。|  
|[hash\_multiset::rbegin](../dotnet/hash-multiset-rbegin-stl-clr.md)|指定已還原的受控制序列開頭。|  
|[hash\_multiset::rehash](../dotnet/hash-multiset-rehash-stl-clr.md)|重新建置雜湊資料表。|  
|[hash\_multiset::rend](../dotnet/hash-multiset-rend-stl-clr.md)|指定已還原的受控制序列結尾。|  
|[hash\_multiset::size](../dotnet/hash-multiset-size-stl-clr.md)|計數項目的數目。|  
|[hash\_multiset::swap](../dotnet/hash-multiset-swap-stl-clr.md)|交換兩個容器的內容。|  
|[hash\_multiset::to\_array](../dotnet/hash-multiset-to-array-stl-clr.md)|複製受控制序列到新陣列。|  
|[hash\_multiset::upper\_bound](../dotnet/hash-multiset-upper-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍結尾。|  
|[hash\_multiset::value\_comp](../dotnet/hash-multiset-value-comp-stl-clr.md)|複製兩個項目值的排序委派。|  
  
|運算子|說明|  
|---------|--------|  
|[hash\_multiset::operator\=](../dotnet/hash-multiset-operator-assign-stl-clr.md)|取代受控制序列。|  
  
## 介面  
  
|介面|說明|  
|--------|--------|  
|<xref:System.ICloneable>|重複物件。|  
|<xref:System.Collections.IEnumerable>|序列傳遞項目。|  
|<xref:System.Collections.ICollection>|維護項目的群組。|  
|<xref:System.Collections.Generic.IEnumerable%601>|序列傳遞型別項目。|  
|<xref:System.Collections.Generic.ICollection%601>|維護型別項目的群組。|  
|IHash\<Key, Value\>|維護泛型容器。|  
  
## 備註  
 物件配置和未使用的記憶體區域的控制項會以個別節點在雙向連結串列的序列。  若要快速存取，物件也會維護指標輸入清單 \(雜湊資料表\)，有效地處理整個清單做為子序列或 Bucket 的變更長度陣列。  它會將項目插入其保持排序修改節點之間的連結 bucket，您可以將節點的內容至另一個。  這表示您可以自由地插入和移除項目，而不會干擾其他項目。  
  
 它會藉由呼叫 [hash\_set::key\_compare](../dotnet/hash-set-key-compare-stl-clr.md)型別所儲存的委派物件控制物件的每一個 bucket。  在建構 hash\_set 時，您可以指定儲存委派物件;如果您不指定委派物件，預設為比較 `operator<=(key_type, key_type)`。  
  
 您可以呼叫成員函式存取所儲存委派物件 [hash\_set::key\_comp](../dotnet/hash-set-key-comp-stl-clr.md)`()`。  這類委派物件必須定義型別之間 [hash\_set::key\_type](../dotnet/hash-set-key-type-stl-clr.md)索引鍵的相等排序。  這表示，任何兩個索引鍵的 `X` 和 `Y`:  
  
 `key_comp()(X, Y)` 會在每次呼叫相同的布林值結果。  
  
 如果 `key_comp()(X, Y) && key_comp()(Y, X)` 為 true，則 `X` 和 `Y` 有相同 Bucket 的項目。  
  
 的行為與 `operator<=(key_type, key_type)`、 `operator>=(key_type, key_type)` 或 `operator==(key_type, key_type)` 所定義 eqivalent 定序的任何排序規則。  
  
 請注意容器確保只有索引鍵有相等排序的項目，而 \(雜湊為相同的整數值\) 在 Bucket 中相鄰的。  不同於樣板類別 [hash\_set](../dotnet/hash-set-stl-clr.md)，樣板類別 `hash_multiset` 物件不需要所有項目的索引鍵是唯一的。\(兩個以上按鍵可能相同 Bucket 的項目\)。  
  
 物件會判斷哪一個 Bucket 中也應該呼叫 [hash\_set::hasher](../dotnet/hash-set-hasher-stl-clr.md)型別所儲存的委派物件包含指定的排序索引鍵。  您可以呼叫成員函式 [hash\_set::hash\_delegate](../dotnet/hash-set-hash-delegate-stl-clr.md)`()` 取得取決於這個機碼值的整數值來存取這個中的物件。  在建構 hash\_set 時，您可以指定儲存委派物件;如果您不指定委派物件，預設為函式 `System::Object::hash_value(key_type)`。  這表示，任何索引鍵的 `X` 和 `Y`:  
  
 `hash_delegate()(X)` 會在每次呼叫相同的整數結果。  
  
 如果 `X` 與 `Y` 相同 Bucket 的項目，則 `hash_delegate()(X)` 會傳回整數結果與 `hash_delegate()(Y)`相同。  
  
 每個項目做為索引鍵和值。  序列表示允許搜尋、一個選擇性項目插入和移除與許多作業的是項目數目獨立序列中的方法 \(常數時間\)\-\-至少在情況下最好。  而且，插入項目不無效 Iterator，，並移除項目無法使用點所移除的項目僅 Iterator。  
  
 如果雜湊值不一致地散發，然而，雜湊資料表可能降低。  非常\-\-對於永遠都會傳回相同值的雜湊函式。\-\-搜尋、插入和移除與項目數目成正比順序 \(線性時間\)。  容器竭力選取合理的雜湊函式、印表機 Bucket 大小和 Hashtable 大小 \(Bucket 總數\)，不過，您可以覆寫任一或全部的索引。  請參閱，例如， [hash\_set::max\_load\_factor](../dotnet/hash-set-max-load-factor-stl-clr.md) 和 [hash\_set::rehash](../dotnet/hash-set-rehash-stl-clr.md)函式。  
  
 hash\_multiset 支援雙向 Iterator，這表示您可以逐步執行至指定的相鄰項目的 Iterator 在受控制序列的項目。  特殊前端節點對應於 [hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)所傳回的 Iterator`()`。  如果您以這個 Iterator 到達受控制序列的最後一個項目。  您可以將 hash\_multiset Iterator 到達前端節點，因此，它與 `end()`會比較相等。  但是，您無法取值 `end()`所傳回的 Iterator。  
  
 請注意您無法直接參考指定的 hash\_multiset 元素其數值位置\-\-該要求隨機存取 Iterator。  
  
 hash\_multiset Iterator 儲存控制代碼關聯的 hash\_multiset 節點，接著儲存的控制代碼關聯的容器。  您只能使用 Iterator 與其關聯的容器物件。  只要其相關聯的 hash\_multiset 節點與陣列 hash\_multiset， hash\_multiset Iterator 保持有效。  而且，有效 Iterator dereferencable\-\-您可以使用它所指派它存取或修改項目的值\-\-只要不等於 `end()`。  
  
 清除或移除元素呼叫它的儲存值的解構函式。  終結容器清除所有項目。  因此，項目型別是 ref 類別的容器確保項目不使用得比容器的。  請注意，然而，容器控制碼做 `not` 終結的項目。  
  
## 需求  
 **標頭：** \<cliext\/hash\_set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)