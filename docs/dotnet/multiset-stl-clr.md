---
title: 多重集 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e01ec2d9c426d6b95b12fe0db9e5a2e328ae1cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)
此範本類別描述控制不同長度序列的項目具有雙向存取的物件。 使用容器`multiset`管理項目序列 （幾乎） 平衡排序樹狀結構的節點，各儲存一個項目。  
  
 在以下描述`GValue`相同`GKey`，這又是相同`Key`後者是 ref 型別，除非在這種情況下很`Key^`。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 Key  
 受控制序列中項目的索引鍵的元件類型。  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[multiset::const_iterator (STL/CLR)](../dotnet/multiset-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[multiset::const_reference (STL/CLR)](../dotnet/multiset-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[multiset::const_reverse_iterator (STL/CLR)](../dotnet/multiset-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[multiset::difference_type (STL/CLR)](../dotnet/multiset-difference-type-stl-clr.md)|兩個項目之間的 （可能是帶正負號） 距離的類型。|  
|[multiset::generic_container (STL/CLR)](../dotnet/multiset-generic-container-stl-clr.md)|容器的泛型介面型別。|  
|[multiset::generic_iterator (STL/CLR)](../dotnet/multiset-generic-iterator-stl-clr.md)|泛型介面，該容器的迭代器類型。|  
|[multiset::generic_reverse_iterator (STL/CLR)](../dotnet/multiset-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器類型。|  
|[multiset::generic_value (STL/CLR)](../dotnet/multiset-generic-value-stl-clr.md)|泛型介面的容器項目的類型。|  
|[multiset::iterator (STL/CLR)](../dotnet/multiset-iterator-stl-clr.md)|受控制序列之迭代器的類型。|  
|[multiset::key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md)|兩個索引鍵排序的委派。|  
|[multiset::key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md)|排序索引鍵的類型。|  
|[multiset::reference (STL/CLR)](../dotnet/multiset-reference-stl-clr.md)|項目的參考類型。|  
|[multiset::reverse_iterator (STL/CLR)](../dotnet/multiset-reverse-iterator-stl-clr.md)|受控制序列的反向迭代器類型。|  
|[multiset::size_type (STL/CLR)](../dotnet/multiset-size-type-stl-clr.md)|（非負數） 之間的距離的兩個項目類型。|  
|[multiset::value_compare (STL/CLR)](../dotnet/multiset-value-compare-stl-clr.md)|兩個項目值順序的委派。|  
|[multiset::value_type (STL/CLR)](../dotnet/multiset-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[multiset::begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[multiset::clear (STL/CLR)](../dotnet/multiset-clear-stl-clr.md)|移除所有項目。|  
|[multiset::count (STL/CLR)](../dotnet/multiset-count-stl-clr.md)|計算指定的索引鍵相符的項目。|  
|[multiset::empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)|測試項目是否不存在。|  
|[multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)|指定受控制序列的結尾。|  
|[multiset::equal_range (STL/CLR)](../dotnet/multiset-equal-range-stl-clr.md)|尋找符合指定之索引鍵的範圍。|  
|[multiset::erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md)|移除位於指定位置的項目。|  
|[multiset::find (STL/CLR)](../dotnet/multiset-find-stl-clr.md)|尋找符合指定之索引鍵的元素。|  
|[multiset::insert (STL/CLR)](../dotnet/multiset-insert-stl-clr.md)|加入項目。|  
|[multiset::key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)|將複製兩個索引鍵的順序委派。|  
|[multiset::lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍開頭。|  
|[multiset::make_value (STL/CLR)](../dotnet/multiset-make-value-stl-clr.md)|建構值物件。|  
|[multiset::multiset (STL/CLR)](../dotnet/multiset-multiset-stl-clr.md)|建構容器物件。|  
|[multiset::rbegin (STL/CLR)](../dotnet/multiset-rbegin-stl-clr.md)|指定反向受控制序列的開頭。|  
|[multiset::rend (STL/CLR)](../dotnet/multiset-rend-stl-clr.md)|指定反向受控制序列的結尾。|  
|[multiset::size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)|計算元素的數目。|  
|[multiset::swap (STL/CLR)](../dotnet/multiset-swap-stl-clr.md)|交換兩個容器的內容。|  
|[multiset::to_array (STL/CLR)](../dotnet/multiset-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
|[multiset::upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍結尾。|  
|[multiset::value_comp (STL/CLR)](../dotnet/multiset-value-comp-stl-clr.md)|將複製兩個項目值的順序委派。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[multiset::operator= (STL/CLR)](../dotnet/multiset-operator-assign-stl-clr.md)|取代受控制的序列。|  
|[operator!= (multiset) (STL/CLR)](../dotnet/operator-inequality-multiset-stl-clr.md)|決定如果`multiset`物件是否不等於另一個`multiset`物件。|  
|[operator< (multiset) (STL/CLR)](../dotnet/operator-less-than-multiset-stl-clr.md)|決定如果`multiset`物件是否小於另一個`multiset`物件。|  
|[operator<= (multiset) (STL/CLR)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)|決定如果`multiset`物件是否小於或等於另一個`multiset`物件。|  
|[operator== (multiset) (STL/CLR)](../dotnet/operator-equality-multiset-stl-clr.md)|決定如果`multiset`物件是否等於另一個`multiset`物件。|  
|[operator> (multiset) (STL/CLR)](../dotnet/operator-greater-than-multiset-stl-clr.md)|決定如果`multiset`物件是否大於另一個`multiset`物件。|  
|[operator>= (multiset) (STL/CLR)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)|決定如果`multiset`物件是否大於或等於另一個`multiset`物件。|  
  
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
  
 物件，排序它藉由呼叫預存的委派類型的物件所控制的序列[multiset:: key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md)。 當您建構 multiset; 時，您可以指定預存的委派物件如果您指定沒有委派的物件時，預設值是比較`operator<(key_type, key_type)`。 您藉由呼叫成員函式中存取這個預存的物件[multiset:: key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)`()`。  
  
 這類委派的物件必須強制執行嚴格弱式排序索引鍵的型別[multiset:: key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md)。 這表示任何兩個索引鍵`X`和`Y`:  
  
 `key_comp()(X, Y)` 傳回的相同的布林值結果，在每次呼叫。  
  
 如果`key_comp()(X, Y)`是 true，則`key_comp()(Y, X)`必須為 false。  
  
 如果`key_comp()(X, Y)`是 true，則`X`稱為排序之前`Y`。  
  
 如果`!key_comp()(X, Y) && !key_comp()(Y, X)`是 true，則`X`和`Y`被視為具有對等順序。  
  
 對於任何項目`X`前面`Y`受控制序列中`key_comp()(Y, X)`為 false。 （預設委派物件索引鍵永遠不會減少值中。）與不同的範本類別是[設定 (STL/CLR)](../dotnet/set-stl-clr.md)，樣板類別的物件`multiset`不需要的所有元素的索引鍵是唯一。 （兩個或多個索引鍵可能有對等順序）。  
  
 每個項目做為金鑰和值。 序列表示允許查閱、 插入和移除任意項目以數字的項目數目之對數成正比的作業順序 （也就是對數時間） 中的方式。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。  
  
 多重集支援雙向迭代器，這表示您可以逐步執行至指定的迭代器，指定受控制序列中的項目相鄰的項目。 特殊的前端節點對應至所傳回的迭代器[multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`。 如果有的話，可以減少此連線到受控制序列中，最後一個元素的迭代器。 可以遞增到前端節點的多重集迭代器，然後它會比較等於`end()`。 您無法取值 （dereference） 所傳回的迭代器，但`end()`。  
  
 請注意，您不能參考多重集的項目，直接指定其數值位置-需要的隨機存取迭代器。  
  
 Multiset 的迭代器會儲存至其相關聯的多重集節點，接著將儲存到其相關聯的容器的控制代碼的控制代碼。 您可以使用迭代器，只能使用其相關聯的容器物件。 只要其相關聯的多重集的節點是某些多重集相關聯的多重集的迭代器會保持有效。 此外，有效的迭代器是 dereferencable--您可用它來存取或修改項目值，它會指定-，只要不等於`end()`。  
  
 清除，或移除項目會呼叫解構函式的儲存值。 終結容器清除所有項目。 因此，其項目類型是 ref 類別的容器可確保，任何項目存留期比長容器。 不過請注意，容器的控制代碼，並會`not`摧毀其項目。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [地圖 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [多重集](../dotnet/multiset-stl-clr.md)   
 [設定 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)