---
title: "設定 (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::set
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9624f08c54629657e7f52c2c688d2083aa557a56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="set-stlclr"></a>set (STL/CLR)
此範本類別描述控制不同長度序列的項目具有雙向存取的物件。 使用容器`set`管理項目序列 （幾乎） 平衡排序樹狀結構的節點，各儲存一個項目。  
  
 在以下描述`GValue`相同`GKey`，這又是相同`Key`後者是 ref 型別，除非在這種情況下很`Key^`。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Key>  
    ref class set  
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
|[set::const_iterator (STL/CLR)](../dotnet/set-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[set::const_reference (STL/CLR)](../dotnet/set-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[set::const_reverse_iterator (STL/CLR)](../dotnet/set-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[set::difference_type (STL/CLR)](../dotnet/set-difference-type-stl-clr.md)|兩個項目之間的 （可能是帶正負號） 距離的類型。|  
|[set::generic_container (STL/CLR)](../dotnet/set-generic-container-stl-clr.md)|容器的泛型介面型別。|  
|[set::generic_iterator (STL/CLR)](../dotnet/set-generic-iterator-stl-clr.md)|泛型介面，該容器的迭代器類型。|  
|[set::generic_reverse_iterator (STL/CLR)](../dotnet/set-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器類型。|  
|[set::generic_value (STL/CLR)](../dotnet/set-generic-value-stl-clr.md)|泛型介面的容器項目的類型。|  
|[set::iterator (STL/CLR)](../dotnet/set-iterator-stl-clr.md)|受控制序列之迭代器的類型。|  
|[set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)|兩個索引鍵排序的委派。|  
|[set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)|排序索引鍵的類型。|  
|[set::reference (STL/CLR)](../dotnet/set-reference-stl-clr.md)|項目的參考類型。|  
|[set::reverse_iterator (STL/CLR)](../dotnet/set-reverse-iterator-stl-clr.md)|受控制序列的反向迭代器類型。|  
|[set::size_type (STL/CLR)](../dotnet/set-size-type-stl-clr.md)|（非負數） 之間的距離的兩個項目類型。|  
|[set::value_compare (STL/CLR)](../dotnet/set-value-compare-stl-clr.md)|兩個項目值順序的委派。|  
|[set::value_type (STL/CLR)](../dotnet/set-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[set::clear (STL/CLR)](../dotnet/set-clear-stl-clr.md)|移除所有項目。|  
|[set::count (STL/CLR)](../dotnet/set-count-stl-clr.md)|計算指定的索引鍵相符的項目。|  
|[set::empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)|測試項目是否不存在。|  
|[set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)|指定受控制序列的結尾。|  
|[set::equal_range (STL/CLR)](../dotnet/set-equal-range-stl-clr.md)|尋找符合指定之索引鍵的範圍。|  
|[set::erase (STL/CLR)](../dotnet/set-erase-stl-clr.md)|移除位於指定位置的項目。|  
|[set::find (STL/CLR)](../dotnet/set-find-stl-clr.md)|尋找符合指定之索引鍵的元素。|  
|[set::insert (STL/CLR)](../dotnet/set-insert-stl-clr.md)|加入項目。|  
|[set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)|將複製兩個索引鍵的順序委派。|  
|[set::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍開頭。|  
|[set::make_value (STL/CLR)](../dotnet/set-make-value-stl-clr.md)|建構值物件。|  
|[set::rbegin (STL/CLR)](../dotnet/set-rbegin-stl-clr.md)|指定反向受控制序列的開頭。|  
|[set::rend (STL/CLR)](../dotnet/set-rend-stl-clr.md)|指定反向受控制序列的結尾。|  
|[set::set (STL/CLR)](../dotnet/set-set-stl-clr.md)|建構容器物件。|  
|[set::size (STL/CLR)](../dotnet/set-size-stl-clr.md)|計算元素的數目。|  
|[set::swap (STL/CLR)](../dotnet/set-swap-stl-clr.md)|交換兩個容器的內容。|  
|[set::to_array (STL/CLR)](../dotnet/set-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
|[set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)|尋找符合指定之索引鍵的範圍結尾。|  
|[set::value_comp (STL/CLR)](../dotnet/set-value-comp-stl-clr.md)|將複製兩個項目值的順序委派。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[set::operator= (STL/CLR)](../dotnet/set-operator-assign-stl-clr.md)|取代受控制的序列。|  
|[operator!= (set) (STL/CLR)](../dotnet/operator-inequality-set-stl-clr.md)|決定如果`set`物件是否不等於另一個`set`物件。|  
|[operator< (set) (STL/CLR)](../dotnet/operator-less-than-set-stl-clr.md)|決定如果`set`物件是否小於另一個`set`物件。|  
|[operator<= (set) (STL/CLR)](../dotnet/operator-less-or-equal-set-stl-clr.md)|決定如果`set`物件是否小於或等於另一個`set`物件。|  
|[operator== (set) (STL/CLR)](../dotnet/operator-equality-set-stl-clr.md)|決定如果`set`物件是否等於另一個`set`物件。|  
|[operator> (set) (STL/CLR)](../dotnet/operator-greater-than-set-stl-clr.md)|決定如果`set`物件是否大於另一個`set`物件。|  
|[operator>= (set) (STL/CLR)](../dotnet/operator-greater-or-equal-set-stl-clr.md)|決定如果`set`物件是否大於或等於另一個`set`物件。|  
  
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
  
 物件，排序它藉由呼叫預存的委派類型的物件所控制的序列[set:: key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)。 當您建構組; 時，您可以指定預存的委派物件如果您指定沒有委派的物件時，預設值是比較`operator<(key_type, key_type)`。 您藉由呼叫成員函式中存取這個預存的物件[set:: key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`。  
  
 這類委派的物件必須強制執行嚴格弱式排序索引鍵的型別[set:: key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)。 這表示任何兩個索引鍵`X`和`Y`:  
  
 `key_comp()(X, Y)`傳回的相同的布林值結果，在每次呼叫。  
  
 如果`key_comp()(X, Y)`是 true，則`key_comp()(Y, X)`必須為 false。  
  
 如果`key_comp()(X, Y)`是 true，則`X`稱為排序之前`Y`。  
  
 如果`!key_comp()(X, Y) && !key_comp()(Y, X)`是 true，則`X`和`Y`被視為具有對等順序。  
  
 對於任何項目`X`前面`Y`受控制序列中`key_comp()(Y, X)`為 false。 （預設委派物件索引鍵永遠不會減少值中。）與不同的範本類別是[設定](../dotnet/set-stl-clr.md)，樣板類別的物件`set`不需要的所有元素的索引鍵是唯一。 （兩個或多個索引鍵可能有對等順序）。  
  
 每個項目做為金鑰和值。 序列表示允許查閱、 插入和移除任意項目以數字的項目數目之對數成正比的作業順序 （也就是對數時間） 中的方式。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。  
  
 一組支援雙向迭代器，這表示您可以逐步執行至指定的迭代器，指定受控制序列中的項目相鄰的項目。 特殊的前端節點對應至所傳回的迭代器[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`。 如果有的話，可以減少此連線到受控制序列中，最後一個元素的迭代器。 可以遞增到達前端節點，一組迭代器，然後它會比較等於`end()`。 您無法取值 （dereference） 所傳回的迭代器，但`end()`。  
  
 請注意，您不能直接提供其數值位置-需要的隨機存取迭代器的設定項目參考。  
  
 集合的迭代器會儲存到其相關聯的集節點，接著會儲存到其相關聯的容器的控制代碼的控制代碼。 您可以使用迭代器，只能使用其相關聯的容器物件。 只要其相關聯的集節點是某些集相關聯集合的迭代器會保持有效。 此外，有效的迭代器是 dereferencable--您可用它來存取或修改項目值，它會指定-，只要不等於`end()`。  
  
 清除，或移除項目會呼叫解構函式的儲存值。 終結容器清除所有項目。 因此，其項目類型是 ref 類別的容器可確保，任何項目存留期比長容器。 不過請注意，容器的控制代碼，並會`not`摧毀其項目。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [地圖 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [設定](../dotnet/set-stl-clr.md)   
 [設定](../dotnet/set-stl-clr.md)   
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)