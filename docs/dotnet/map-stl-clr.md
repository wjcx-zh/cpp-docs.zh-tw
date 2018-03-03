---
title: "地圖 (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::map
dev_langs:
- C++
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c90fcb415b186257cd2aef801867918b367413b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="map-stlclr"></a>map (STL/CLR)
此範本類別描述控制不同長度序列的項目具有雙向存取的物件。 使用容器`map`管理項目序列 （幾乎） 平衡排序樹狀結構的節點，各儲存一個項目。 項目所組成的索引鍵，排序順序，以及對應的值，會大功告成了。  
  
 在以下描述`GValue`相同：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey`等同於`Key`後者是 ref 型別，除非在這種情況下很`Key^`  
  
 `GMapped`等同於`Mapped`後者是 ref 型別，除非在這種情況下很`Mapped^`  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 Key  
 受控制序列中項目的索引鍵的元件類型。  
  
 對應  
 受控制序列中項目的其他元件的類型。  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[map::const_iterator (STL/CLR)](../dotnet/map-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[map::const_reference (STL/CLR)](../dotnet/map-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[map::const_reverse_iterator (STL/CLR)](../dotnet/map-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[map::difference_type (STL/CLR)](../dotnet/map-difference-type-stl-clr.md)|兩個項目之間的 （可能是帶正負號） 距離的類型。|  
|[map::generic_container (STL/CLR)](../dotnet/map-generic-container-stl-clr.md)|容器的泛型介面型別。|  
|[map::generic_iterator (STL/CLR)](../dotnet/map-generic-iterator-stl-clr.md)|泛型介面，該容器的迭代器類型。|  
|[map::generic_reverse_iterator (STL/CLR)](../dotnet/map-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器類型。|  
|[map::generic_value (STL/CLR)](../dotnet/map-generic-value-stl-clr.md)|泛型介面的容器項目的類型。|  
|[map::iterator (STL/CLR)](../dotnet/map-iterator-stl-clr.md)|受控制序列之迭代器的類型。|  
|[map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)|兩個索引鍵排序的委派。|  
|[map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)|排序索引鍵的類型。|  
|[map::mapped_type (STL/CLR)](../dotnet/map-mapped-type-stl-clr.md)|每個索引鍵相關聯的對應值的型別。|  
|[map::reference (STL/CLR)](../dotnet/map-reference-stl-clr.md)|項目的參考類型。|  
|[map::reverse_iterator (STL/CLR)](../dotnet/map-reverse-iterator-stl-clr.md)|受控制序列的反向迭代器類型。|  
|[map::size_type (STL/CLR)](../dotnet/map-size-type-stl-clr.md)|（非負數） 之間的距離的兩個項目類型。|  
|[map::value_compare (STL/CLR)](../dotnet/map-value-compare-stl-clr.md)|兩個項目值順序的委派。|  
|[map::value_type (STL/CLR)](../dotnet/map-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[map::begin (STL/CLR)](../dotnet/map-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[map::clear (STL/CLR)](../dotnet/map-clear-stl-clr.md)|移除所有項目。|  
|[map::count (STL/CLR)](../dotnet/map-count-stl-clr.md)|計算指定的索引鍵相符的項目。|  
|[map::empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)|測試項目是否不存在。|  
|[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)|指定受控制序列的結尾。|  
|[map::equal_range (STL/CLR)](../dotnet/map-equal-range-stl-clr.md)|尋找符合指定之索引鍵的範圍。|  
|[map::erase (STL/CLR)](../dotnet/map-erase-stl-clr.md)|移除位於指定位置的項目。|  
|[map::find (STL/CLR)](../dotnet/map-find-stl-clr.md)|尋找符合指定之索引鍵的元素。|  
|[map::insert (STL/CLR)](../dotnet/map-insert-stl-clr.md)|加入項目。|  
|[map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)|將複製兩個索引鍵的順序委派。|  
|[map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍開頭。|  
|[map::make_value (STL/CLR)](../dotnet/map-make-value-stl-clr.md)|建構值物件。|  
|[map::map (STL/CLR)](../dotnet/map-map-stl-clr.md)|建構容器物件。|  
|[map::rbegin (STL/CLR)](../dotnet/map-rbegin-stl-clr.md)|指定反向受控制序列的開頭。|  
|[map::rend (STL/CLR)](../dotnet/map-rend-stl-clr.md)|指定反向受控制序列的結尾。|  
|[map::size (STL/CLR)](../dotnet/map-size-stl-clr.md)|計算元素的數目。|  
|[map::swap (STL/CLR)](../dotnet/map-swap-stl-clr.md)|交換兩個容器的內容。|  
|[map::to_array (STL/CLR)](../dotnet/map-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
|[map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍結尾。|  
|[map::value_comp (STL/CLR)](../dotnet/map-value-comp-stl-clr.md)|將複製兩個項目值的順序委派。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[map::operator= (STL/CLR)](../dotnet/map-operator-assign-stl-clr.md)|取代受控制的序列。|  
|[map::operator (STL/CLR)](../dotnet/map-operator-stl-clr.md)|將索引鍵對應至其相關聯的對應值。|  
|[operator!= (map) (STL/CLR)](../dotnet/operator-inequality-map-stl-clr.md)|決定如果`map`物件是否不等於另一個`map`物件。|  
|[operator< (map) (STL/CLR)](../dotnet/operator-less-than-map-stl-clr.md)|決定如果`map`物件是否小於另一個`map`物件。|  
|[operator<= (map) (STL/CLR)](../dotnet/operator-less-or-equal-map-stl-clr.md)|決定如果`map`物件是否小於或等於另一個`map`物件。|  
|[operator== (map) (STL/CLR)](../dotnet/operator-equality-map-stl-clr.md)|決定如果`map`物件是否等於另一個`map`物件。|  
|[operator> (map) (STL/CLR)](../dotnet/operator-greater-than-map-stl-clr.md)|決定如果`map`物件是否大於另一個`map`物件。|  
|[operator>= (map) (STL/CLR)](../dotnet/operator-greater-or-equal-map-stl-clr.md)|決定如果`map`物件是否大於或等於另一個`map`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|<xref:System.Collections.IEnumerable>|項目順序。|  
|<xref:System.Collections.ICollection>|維護群組的項目。|  
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的項目順序。|  
|<xref:System.Collections.Generic.ICollection%601>|維護群組的具類型的項目。|  
|<xref:System.Collections.Generic.IDictionary%602>|維護群組 {索引鍵的值} 配對。|  
|ITree < 索引鍵、 值 >|維護泛型容器。|  
  
## <a name="remarks"></a>備註  
 物件可配置及釋放它做為個別的節點所控制的序列的儲存體。 它會將元素插入 （幾乎） 平衡樹狀目錄中，它會保留排序會改變節點，而非由複製到另一個節點的內容之間的連結。 這表示您可以插入和移除項目，自由地不干擾其餘項目。  
  
 物件，排序它藉由呼叫預存的委派類型的物件所控制的序列[map:: key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)。 當您建構對應時，您可以指定預存的委派物件如果您指定沒有委派的物件時，預設值是比較`operator<(key_type, key_type)`。 您藉由呼叫成員函式中存取這個預存的物件[map:: key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)`()`。  
  
 這類委派的物件必須強制執行嚴格弱式排序索引鍵的型別[map:: key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)。 這表示任何兩個索引鍵`X`和`Y`:  
  
 `key_comp()(X, Y)`傳回的相同的布林值結果，在每次呼叫。  
  
 如果`key_comp()(X, Y)`是 true，則`key_comp()(Y, X)`必須為 false。  
  
 如果`key_comp()(X, Y)`是 true，則`X`稱為排序之前`Y`。  
  
 如果`!key_comp()(X, Y) && !key_comp()(Y, X)`是 true，則`X`和`Y`被視為具有對等順序。  
  
 對於任何項目`X`前面`Y`受控制序列中`key_comp()(Y, X)`為 false。 （預設委派物件索引鍵永遠不會減少值中。）與不同的範本類別是[對應](../dotnet/map-stl-clr.md)，樣板類別的物件`map`不需要的所有元素的索引鍵是唯一。 （兩個或多個索引鍵可能有對等順序）。  
  
 每個項目包含個別的索引鍵和對應的值。 序列表示允許查閱、 插入和移除任意項目以數字的項目數目之對數成正比的作業順序 （也就是對數時間） 中的方式。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。  
  
 對應支援雙向迭代器，這表示您可以逐步執行至指定的迭代器，指定受控制序列中的項目相鄰的項目。 特殊的前端節點對應至所傳回的迭代器[map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`。 如果有的話，可以減少此連線到受控制序列中，最後一個元素的迭代器。 您可以遞增到前端節點的對應迭代器，然後它會比較等於`end()`。 您無法取值 （dereference） 所傳回的迭代器，但`end()`。  
  
 請注意，您不能直接提供其數值位置-需要的隨機存取迭代器的對應項目參考。  
  
 對應的迭代器會儲存其相關聯的對應 節點，接著會儲存到其相關聯的容器的控制代碼的控制代碼。 您可以使用迭代器，只能使用其相關聯的容器物件。 只要其相關聯的對應節點是與部分地圖相關聯的對應迭代器會保持有效。 此外，有效的迭代器是 dereferencable--您可用它來存取或修改項目值，它會指定-，只要不等於`end()`。  
  
 清除，或移除項目會呼叫解構函式的儲存值。 終結容器清除所有項目。 因此，其項目類型是 ref 類別的容器可確保，任何項目存留期比長容器。 不過請注意，容器的控制代碼，並會`not`摧毀其項目。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [對應](../dotnet/map-stl-clr.md)   
 [多重集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [設定 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)