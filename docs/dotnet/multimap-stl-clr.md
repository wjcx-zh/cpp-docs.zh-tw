---
title: "multimap (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multimap
dev_langs:
- C++
helpviewer_keywords:
- <map> header [STL/CLR]
- <cliext/map> header [STL/CLR]
- multimap class [STL/CLR]
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2c42fc8d71871a70e3a2d3ffa93a78a4e42d2f53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multimap-stlclr"></a>multimap (STL/CLR)
此範本類別描述控制不同長度序列的項目具有雙向存取的物件。 使用容器`multimap`管理項目序列 （幾乎） 平衡排序樹狀結構的節點，各儲存一個項目。 項目所組成的索引鍵，排序順序，以及對應的值，會大功告成了。  
  
 在以下描述`GValue`相同：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey`等同於`Key`後者是 ref 型別，除非在這種情況下很`Key^`  
  
 `GMapped`等同於`Mapped`後者是 ref 型別，除非在這種情況下很`Mapped^`  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 Key  
 受控制序列中項目的索引鍵的元件類型。  
  
 對應  
 受控制序列中項目的其他元件的類型。  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[multimap::const_iterator (STL/CLR)](../dotnet/multimap-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[multimap::const_reference (STL/CLR)](../dotnet/multimap-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[multimap::const_reverse_iterator (STL/CLR)](../dotnet/multimap-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[multimap::difference_type (STL/CLR)](../dotnet/multimap-difference-type-stl-clr.md)|兩個項目之間的 （可能是帶正負號） 距離的類型。|  
|[multimap::generic_container (STL/CLR)](../dotnet/multimap-generic-container-stl-clr.md)|容器的泛型介面型別。|  
|[multimap::generic_iterator (STL/CLR)](../dotnet/multimap-generic-iterator-stl-clr.md)|泛型介面，該容器的迭代器類型。|  
|[multimap::generic_reverse_iterator (STL/CLR)](../dotnet/multimap-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器類型。|  
|[multimap::generic_value (STL/CLR)](../dotnet/multimap-generic-value-stl-clr.md)|泛型介面的容器項目的類型。|  
|[multimap::iterator (STL/CLR)](../dotnet/multimap-iterator-stl-clr.md)|受控制序列之迭代器的類型。|  
|[multimap::key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md)|兩個索引鍵排序的委派。|  
|[multimap::key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md)|排序索引鍵的類型。|  
|[multimap::mapped_type (STL/CLR)](../dotnet/multimap-mapped-type-stl-clr.md)|每個索引鍵相關聯的對應值的型別。|  
|[multimap::reference (STL/CLR)](../dotnet/multimap-reference-stl-clr.md)|項目的參考類型。|  
|[multimap::reverse_iterator (STL/CLR)](../dotnet/multimap-reverse-iterator-stl-clr.md)|受控制序列的反向迭代器類型。|  
|[multimap::size_type (STL/CLR)](../dotnet/multimap-size-type-stl-clr.md)|（非負數） 之間的距離的兩個項目類型。|  
|[multimap::value_compare (STL/CLR)](../dotnet/multimap-value-compare-stl-clr.md)|兩個項目值順序的委派。|  
|[multimap::value_type (STL/CLR)](../dotnet/multimap-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[multimap::begin (STL/CLR)](../dotnet/multimap-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[multimap::clear (STL/CLR)](../dotnet/multimap-clear-stl-clr.md)|移除所有項目。|  
|[multimap::count (STL/CLR)](../dotnet/multimap-count-stl-clr.md)|計算指定的索引鍵相符的項目。|  
|[multimap::empty (STL/CLR)](../dotnet/multimap-empty-stl-clr.md)|測試項目是否不存在。|  
|[multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)|指定受控制序列的結尾。|  
|[multimap::equal_range (STL/CLR)](../dotnet/multimap-equal-range-stl-clr.md)|尋找符合指定之索引鍵的範圍。|  
|[multimap::erase (STL/CLR)](../dotnet/multimap-erase-stl-clr.md)|移除位於指定位置的項目。|  
|[multimap::find (STL/CLR)](../dotnet/multimap-find-stl-clr.md)|尋找符合指定之索引鍵的元素。|  
|[multimap::insert (STL/CLR)](../dotnet/multimap-insert-stl-clr.md)|加入項目。|  
|[multimap::key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)|將複製兩個索引鍵的順序委派。|  
|[multimap::lower_bound (STL/CLR)](../dotnet/multimap-lower-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍開頭。|  
|[multimap::make_value (STL/CLR)](../dotnet/multimap-make-value-stl-clr.md)|建構值物件。|  
|[multimap::multimap (STL/CLR)](../dotnet/multimap-multimap-stl-clr.md)|建構容器物件。|  
|[multimap::rbegin (STL/CLR)](../dotnet/multimap-rbegin-stl-clr.md)|指定反向受控制序列的開頭。|  
|[multimap::rend (STL/CLR)](../dotnet/multimap-rend-stl-clr.md)|指定反向受控制序列的結尾。|  
|[multimap::size (STL/CLR)](../dotnet/multimap-size-stl-clr.md)|計算元素的數目。|  
|[multimap::swap (STL/CLR)](../dotnet/multimap-swap-stl-clr.md)|交換兩個容器的內容。|  
|[multimap::to_array (STL/CLR)](../dotnet/multimap-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
|[multimap::upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍結尾。|  
|[multimap::value_comp (STL/CLR)](../dotnet/multimap-value-comp-stl-clr.md)|將複製兩個項目值的順序委派。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[multimap::operator= (STL/CLR)](../dotnet/multimap-operator-assign-stl-clr.md)|取代受控制的序列。|  
|[operator!= (multimap) (STL/CLR)](../dotnet/operator-inequality-multimap-stl-clr.md)|決定如果`multimap`物件是否不等於另一個`multimap`物件。|  
|[operator< (multimap) (STL/CLR)](../dotnet/operator-less-than-multimap-stl-clr.md)|決定如果`multimap`物件是否小於另一個`multimap`物件。|  
|[operator<= (multimap) (STL/CLR)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)|決定如果`multimap`物件是否小於或等於另一個`multimap`物件。|  
|[operator== (multimap) (STL/CLR)](../dotnet/operator-equality-multimap-stl-clr.md)|決定如果`multimap`物件是否等於另一個`multimap`物件。|  
|[operator> (multimap) (STL/CLR)](../dotnet/operator-greater-than-multimap-stl-clr.md)|決定如果`multimap`物件是否大於另一個`multimap`物件。|  
|[operator>= (multimap) (STL/CLR)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)|決定如果`multimap`物件是否大於或等於另一個`multimap`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|<xref:System.Collections.IEnumerable>|項目順序。|  
|<xref:System.Collections.ICollection>|維護群組的項目。|  
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的項目順序。|  
|<xref:System.Collections.Generic.ICollection%601>|維護群組的具類型的項目。|  
|ITree\<索引鍵、 值 >|維護泛型容器。|  
  
## <a name="remarks"></a>備註  
 物件可配置及釋放它做為個別的節點所控制的序列的儲存體。 它會將元素插入 （幾乎） 平衡樹狀目錄中，它會保留排序會改變節點，而非由複製到另一個節點的內容之間的連結。 這表示您可以插入和移除項目，自由地不干擾其餘項目。  
  
 物件，排序它藉由呼叫預存的委派類型的物件所控制的序列[multimap:: key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md)。 當您建構 multimap; 時，您可以指定預存的委派物件如果您指定沒有委派的物件時，預設值是比較`operator<(key_type, key_type)`。 您藉由呼叫成員函式中存取這個預存的物件[multimap:: key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)`()`。  
  
 這類委派的物件必須強制執行嚴格弱式排序索引鍵的型別[multimap:: key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md)。 這表示任何兩個索引鍵`X`和`Y`:  
  
 `key_comp()(X, Y)`傳回的相同的布林值結果，在每次呼叫。  
  
 如果`key_comp()(X, Y)`是 true，則`key_comp()(Y, X)`必須為 false。  
  
 如果`key_comp()(X, Y)`是 true，則`X`稱為排序之前`Y`。  
  
 如果`!key_comp()(X, Y) && !key_comp()(Y, X)`是 true，則`X`和`Y`被視為具有對等順序。  
  
 對於任何項目`X`前面`Y`受控制序列中`key_comp()(Y, X)`為 false。 （預設委派物件索引鍵永遠不會減少值中。）與不同的範本類別是[對應 (STL/CLR)](../dotnet/map-stl-clr.md)，樣板類別的物件`multimap`不需要的所有元素的索引鍵是唯一。 （兩個或多個索引鍵可能有對等順序）。  
  
 每個項目包含個別的索引鍵和對應的值。 序列表示允許查閱、 插入和移除任意項目以數字的項目數目之對數成正比的作業順序 （也就是對數時間） 中的方式。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。  
  
 Multimap 支援雙向迭代器，這表示您可以逐步執行至指定的迭代器，指定受控制序列中的項目相鄰的項目。 特殊的前端節點對應至所傳回的迭代器[multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`。 如果有的話，可以減少此連線到受控制序列中，最後一個元素的迭代器。 可以遞增到前端節點的 multimap 迭代器，然後它會比較等於`end()`。 您無法取值 （dereference） 所傳回的迭代器，但`end()`。  
  
 請注意，您不能參考 multimap 的項目，直接指定其數值位置-需要的隨機存取迭代器。  
  
 Multimap 的迭代器會儲存至其相關聯的 multimap 節點，接著將儲存到其相關聯的容器的控制代碼的控制代碼。 您可以使用迭代器，只能使用其相關聯的容器物件。 只要其相關聯的 multimap 節點都與某些 multimap multimap 的迭代器會保持有效。 此外，有效的迭代器是 dereferencable--您可用它來存取或修改項目值，它會指定-，只要不等於`end()`。  
  
 清除，或移除項目會呼叫解構函式的儲存值。 終結容器清除所有項目。 因此，其項目類型是 ref 類別的容器可確保，任何項目存留期比長容器。 不過請注意，容器的控制代碼，並會`not`摧毀其項目。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [地圖 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [多重集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [設定 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)