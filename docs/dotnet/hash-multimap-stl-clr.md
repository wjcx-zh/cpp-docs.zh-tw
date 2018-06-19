---
title: hash_multimap (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multimap
dev_langs:
- C++
helpviewer_keywords:
- hash_multimap class [STL/CLR]
- <cliext/hash_map> header [STL/CLR]
- <hash_map> header [STL/CLR]
ms.assetid: cd78687b-8a05-48e0-9d22-8b8194ae3b0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 027ed43936e4335819f95d10050de37570e6a679
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137989"
---
# <a name="hashmultimap-stlclr"></a>hash_multimap (STL/CLR)
此範本類別描述控制不同長度序列的項目具有雙向存取的物件。 使用容器`hash_multimap`若要管理的項目序列的雜湊表，儲存雙向的每個資料表項目連結清單節點，以及儲存一個項目每個節點。 項目所組成的索引鍵，排序順序，以及對應的值，會大功告成了。  
  
 在以下描述`GValue`相同：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey` 等同於`Key`後者是 ref 型別，除非在這種情況下很 `Key^`  
  
 `GMapped` 等同於`Mapped`後者是 ref 型別，除非在這種情況下很 `Mapped^`  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class hash_multimap  
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
  
#### <a name="parameters"></a>參數  
 Key  
 受控制序列中項目的索引鍵的元件類型。  
  
 對應  
 受控制序列中項目的其他元件的類型。  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[hash_multimap::const_iterator (STL/CLR)](../dotnet/hash-multimap-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[hash_multimap::const_reference (STL/CLR)](../dotnet/hash-multimap-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[hash_multimap::const_reverse_iterator (STL/CLR)](../dotnet/hash-multimap-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[hash_multimap::difference_type (STL/CLR)](../dotnet/hash-multimap-difference-type-stl-clr.md)|兩個項目之間的 （可能是帶正負號） 距離的類型。|  
|[hash_multimap::generic_container (STL/CLR)](../dotnet/hash-multimap-generic-container-stl-clr.md)|容器的泛型介面型別。|  
|[hash_multimap::generic_iterator (STL/CLR)](../dotnet/hash-multimap-generic-iterator-stl-clr.md)|泛型介面，該容器的迭代器類型。|  
|[hash_multimap::generic_reverse_iterator (STL/CLR)](../dotnet/hash-multimap-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器類型。|  
|[hash_multimap::generic_value (STL/CLR)](../dotnet/hash-multimap-generic-value-stl-clr.md)|泛型介面的容器項目的類型。|  
|[hash_multimap::hasher (STL/CLR)](../dotnet/hash-multimap-hasher-stl-clr.md)|索引鍵雜湊的委派。|  
|[hash_multimap::iterator (STL/CLR)](../dotnet/hash-multimap-iterator-stl-clr.md)|受控制序列之迭代器的類型。|  
|[hash_multimap::key_compare (STL/CLR)](../dotnet/hash-multimap-key-compare-stl-clr.md)|兩個索引鍵排序的委派。|  
|[hash_multimap::key_type (STL/CLR)](../dotnet/hash-multimap-key-type-stl-clr.md)|排序索引鍵的類型。|  
|[hash_multimap::mapped_type (STL/CLR)](../dotnet/hash-multimap-mapped-type-stl-clr.md)|每個索引鍵相關聯的對應值的型別。|  
|[hash_multimap::reference (STL/CLR)](../dotnet/hash-multimap-reference-stl-clr.md)|項目的參考類型。|  
|[hash_multimap::reverse_iterator (STL/CLR)](../dotnet/hash-multimap-reverse-iterator-stl-clr.md)|受控制序列的反向迭代器類型。|  
|[hash_multimap::size_type (STL/CLR)](../dotnet/hash-multimap-size-type-stl-clr.md)|（非負數） 之間的距離的兩個項目類型。|  
|[hash_multimap::value_compare (STL/CLR)](../dotnet/hash-multimap-value-compare-stl-clr.md)|兩個項目值順序的委派。|  
|[hash_multimap::value_type (STL/CLR)](../dotnet/hash-multimap-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[hash_multimap::begin (STL/CLR)](../dotnet/hash-multimap-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[hash_multimap::bucket_count (STL/CLR)](../dotnet/hash-multimap-bucket-count-stl-clr.md)|計算值區數目。|  
|[hash_multimap::clear (STL/CLR)](../dotnet/hash-multimap-clear-stl-clr.md)|移除所有項目。|  
|[hash_multimap::count (STL/CLR)](../dotnet/hash-multimap-count-stl-clr.md)|計算指定的索引鍵相符的項目。|  
|[hash_multimap::empty (STL/CLR)](../dotnet/hash-multimap-empty-stl-clr.md)|測試項目是否不存在。|  
|[hash_multimap::end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)|指定受控制序列的結尾。|  
|[hash_multimap::equal_range (STL/CLR)](../dotnet/hash-multimap-equal-range-stl-clr.md)|尋找符合指定之索引鍵的範圍。|  
|[hash_multimap::erase (STL/CLR)](../dotnet/hash-multimap-erase-stl-clr.md)|移除位於指定位置的項目。|  
|[hash_multimap::find (STL/CLR)](../dotnet/hash-multimap-find-stl-clr.md)|尋找符合指定之索引鍵的元素。|  
|[hash_multimap::hash_delegate (STL/CLR)](../dotnet/hash-multimap-hash-delegate-stl-clr.md)|將複製的索引鍵的雜湊的委派。|  
|[hash_multimap::hash_multimap (STL/CLR)](../dotnet/hash-multimap-hash-multimap-stl-clr.md)|建構容器物件。|  
|[hash_multimap::insert (STL/CLR)](../dotnet/hash-multimap-insert-stl-clr.md)|加入項目。|  
|[hash_multimap::key_comp (STL/CLR)](../dotnet/hash-multimap-key-comp-stl-clr.md)|將複製兩個索引鍵的順序委派。|  
|[hash_multimap::load_factor (STL/CLR)](../dotnet/hash-multimap-load-factor-stl-clr.md)|計算每個值區的平均項目數。|  
|[hash_multimap::lower_bound (STL/CLR)](../dotnet/hash-multimap-lower-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍開頭。|  
|[hash_multimap::make_value (STL/CLR)](../dotnet/hash-multimap-make-value-stl-clr.md)|建構值物件。|  
|[hash_multimap::max_load_factor (STL/CLR)](../dotnet/hash-multimap-max-load-factor-stl-clr.md)|取得或設定每個 Bucket 最大項目數。|  
|[hash_multimap::rbegin (STL/CLR)](../dotnet/hash-multimap-rbegin-stl-clr.md)|指定反向受控制序列的開頭。|  
|[hash_multimap::rehash (STL/CLR)](../dotnet/hash-multimap-rehash-stl-clr.md)|重建雜湊資料表。|  
|[hash_multimap::rend (STL/CLR)](../dotnet/hash-multimap-rend-stl-clr.md)|指定反向受控制序列的結尾。|  
|[hash_multimap::size (STL/CLR)](../dotnet/hash-multimap-size-stl-clr.md)|計算元素的數目。|  
|[hash_multimap::swap (STL/CLR)](../dotnet/hash-multimap-swap-stl-clr.md)|交換兩個容器的內容。|  
|[hash_multimap::to_array (STL/CLR)](../dotnet/hash-multimap-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
|[hash_multimap::upper_bound (STL/CLR)](../dotnet/hash-multimap-upper-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍結尾。|  
|[hash_multimap::value_comp (STL/CLR)](../dotnet/hash-multimap-value-comp-stl-clr.md)|將複製兩個項目值的順序委派。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[hash_multimap::operator= (STL/CLR)](../dotnet/hash-multimap-operator-assign-stl-clr.md)|取代受控制的序列。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|<xref:System.Collections.IEnumerable>|項目順序。|  
|<xref:System.Collections.ICollection>|維護群組的項目。|  
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的項目順序。|  
|<xref:System.Collections.Generic.ICollection%601>|維護群組的具類型的項目。|  
|IHash\<索引鍵、 值 >|維護泛型容器。|  
  
## <a name="remarks"></a>備註  
 物件可配置及釋放它為雙向連結清單中的個別節點所控制的序列的儲存體。 若要加快存取速度，物件也會維護有效管理整份清單為一連串個子，指標至清單 （雜湊資料表） 的變動長度陣列或值區。 它會將項目插入藉由改變節點，而非由複製到另一個節點的內容之間的連結會保持已排序的值區。 這表示您可以插入和移除項目，自由地不干擾其餘項目。  
  
 物件，排序它所控制藉由呼叫預存的委派物件類型的每個貯體[hash_set:: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md)。 當您建構 hash_set; 時，您可以指定預存的委派物件如果您指定沒有委派的物件時，預設值是比較`operator<=(key_type, key_type)`。  
  
 您藉由呼叫成員函式存取的預存的委派物件[hash_set:: key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`。 這類委派的物件必須定義索引鍵的型別之間的對等順序[hash_set:: key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)。 這表示任何兩個索引鍵`X`和`Y`:  
  
 `key_comp()(X, Y)` 傳回的相同的布林值結果，在每次呼叫。  
  
 如果`key_comp()(X, Y) && key_comp()(Y, X)`是 true，則`X`和`Y`被視為具有對等順序。  
  
 如同任何排序規則`operator<=(key_type, key_type)`，`operator>=(key_type, key_type)`或`operator==(key_type, key_type)`eqivalent 順序會定義。  
  
 請注意，容器可確保只有，項目之索引鍵具有對等順序 （和為相同的整數值的雜湊） 都是相鄰的貯體中。 與不同的範本類別是[hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)，樣板類別的物件`hash_multimap`不需要的所有元素的索引鍵是唯一。 （兩個或多個索引鍵可能有對等順序）。  
  
 物件可讓您判斷哪一個 bucket 應該藉由呼叫預存的委派類型的物件包含指定的排序索引鍵[hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)。 您藉由呼叫成員函式中存取這個預存的物件[hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()`取得索引鍵的值而定的整數值。 當您建構 hash_set; 時，您可以指定預存的委派物件如果您指定沒有委派的物件時，預設值是函式`System::Object::hash_value(key_type)`。 這表示任何索引鍵`X`和`Y`:  
  
 `hash_delegate()(X)` 在每次呼叫會傳回相同的整數結果。  
  
 如果`X`和`Y`具有對等順序，然後`hash_delegate()(X)`應該會傳回相同的整數結果`hash_delegate()(Y)`。  
  
 每個項目包含個別的索引鍵和對應的值。 序列表示允許查閱、 插入和移除任意項目使用的作業數目無關的 （常數時間）-序列中的項目數至少在最佳情況下的方式。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。  
  
 如果雜湊的值不一致的方式散發，不過，可以變質雜湊表。 在極端的做法是-雜湊函式一律會傳回相同的值-查閱、 插入和移除為順序 （線性時間） 中的項目數目成正比。 容器儘量選擇合理的雜湊函式、 值區平均大小和雜湊表大小 （的貯體的總數目），但是您可以覆寫任何或所有的這些選項。 請參閱，例如，函式[hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md)和[hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md)。  
  
 Hash_multimap 支援雙向迭代器，這表示您可以逐步執行至指定的迭代器，指定受控制序列中的項目相鄰的項目。 特殊的前端節點對應至所傳回的迭代器[hash_multimap:: end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)`()`。 如果有的話，可以減少此連線到受控制序列中，最後一個元素的迭代器。 您可以遞增到前端節點之後，hash_multimap 迭代器，然後它會比較等於`end()`。 您無法取值 （dereference） 所傳回的迭代器，但`end()`。  
  
 請注意，您無法直接指定其數值位置-需要的隨機存取迭代器 hash_multimap 項目參考。  
  
 Hash_multimap 的迭代器會儲存到其相關聯的 hash_multimap 節點，接著會儲存到其相關聯的容器的控制代碼的控制代碼。 您可以使用迭代器，只能使用其相關聯的容器物件。 只要其相關聯的 hash_multimap 節點都與某些 hash_multimap 的 hash_multimap 迭代器會保持有效。 此外，有效的迭代器是 dereferencable--您可用它來存取或修改項目值，它會指定-，只要不等於`end()`。  
  
 清除，或移除項目會呼叫解構函式的儲存值。 終結容器清除所有項目。 因此，其項目類型是 ref 類別的容器可確保，任何項目存留期比長容器。 不過請注意，容器的控制代碼，並會`not`摧毀其項目。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_map >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [地圖 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [多重集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [設定 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)