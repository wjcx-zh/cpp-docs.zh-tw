---
title: 地圖 (STL/CLR) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map
- cliext::map::begin
- cliext::map::clear
- cliext::map::const_iterator
- cliext::map::const_reference
- cliext::map::const_reverse_iterator
- cliext::map::count
- cliext::map::difference_type
- cliext::map::empty
- cliext::map::end
- cliext::map::equal_range
- cliext::map::erase
- cliext::map::find
- cliext::map::generic_container
- cliext::map::generic_iterator
- cliext::map::generic_reverse_iterator
- cliext::map::generic_value
- cliext::map::insert
- cliext::map::iterator
- cliext::map::key_comp
- cliext::map::key_compare
- cliext::map::key_type
- cliext::map::lower_bound
- cliext::map::make_value
- cliext::map::map
- cliext::map::mapped_type
- cliext::map::operator=
- cliext::map::operator
- cliext::map::rbegin
- cliext::map::reference
- cliext::map::rend
- cliext::map::reverse_iterator
- cliext::map::size
- cliext::map::size_type
- cliext::map::swap
- cliext::map::to_array
- cliext::map::upper_bound
- cliext::map::value_comp
- cliext::map::value_compare
- cliext::map::value_type
- cliext::operator!= (map)
- cliext::operator< (map)
- cliext::operator<= (map)
- cliext::operator== (map)
- cliext::operator> (map)
- cliext::operator>= (map)
dev_langs:
- C++
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
- operator!= (map) member [STL/CLR]
- operator< (map) member [STL/CLR]
- operator<= (map) member [STL/CLR]
- operator== (map) member [STL/CLR]
- operator> (map) member [STL/CLR]
- operator>= (map) member [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 99a809753b244f442bf2eb321c58f4a07c5ba546
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376348"
---
# <a name="map-stlclr"></a>map (STL/CLR)
此範本類別描述控制不同長度序列的項目可雙向存取的物件。 使用容器`map`來管理一系列的項目為 （幾乎） 平衡排序樹狀結構的節點，各儲存一個項目。 項目所組成的索引鍵，排序順序，以及對應的值，其中會好好體驗吧。  
  
 在下面的描述`GValue`相同：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey` 等同於*金鑰*後者是 ref 型別，除非在此情況下是 `Key^`  
  
 `GMapped` 等同於*對應*後者是 ref 型別，除非在此情況下是 `Mapped^`  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
### <a name="parameters"></a>參數  
 *Key*  
 受控制序列中項目的索引鍵的元件型別。  
  
 *對應*  
 受控制序列中項目的其他元件的型別。  

## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="declarations"></a>宣告
  
|類型定義|描述|  
|---------------------|-----------------|  
|[map::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|  
|[map::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|  
|[map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|  
|[map::difference_type (STL/CLR)](#difference_type)|（可能是帶正負號） 的距離兩個項目之間的型別。|  
|[map::generic_container (STL/CLR)](#generic_container)|容器的泛型介面型別。|  
|[map::generic_iterator (STL/CLR)](#generic_iterator)|泛型介面，該容器的迭代器類型。|  
|[map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面的反向迭代器類型。|  
|[map::generic_value (STL/CLR)](#generic_value)|容器的泛型介面的項目型別。|  
|[map::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|  
|[map::key_compare (STL/CLR)](#key_compare)|兩個索引鍵排序委派。|  
|[map::key_type (STL/CLR)](#key_type)|排序索引鍵的類型。|  
|[map::mapped_type (STL/CLR)](#mapped_type)|每個索引鍵相關聯的對應值的型別。|  
|[map::reference (STL/CLR)](#reference)|項目的參考類型。|  
|[map::reverse_iterator (STL/CLR)](#reverse_iterator)|受控制序列的反向迭代器類型。|  
|[map::size_type (STL/CLR)](#size_type)|（非負數） 之間的距離兩個項目型別。|  
|[map::value_compare (STL/CLR)](#value_compare)|兩個元素值排序委派。|  
|[map::value_type (STL/CLR)](#value_type)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[map::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|  
|[map::clear (STL/CLR)](#clear)|移除所有項目。|  
|[map::count (STL/CLR)](#count)|會計算符合指定索引鍵的項目。|  
|[map::empty (STL/CLR)](#empty)|測試項目是否不存在。|  
|[map::end (STL/CLR)](#end)|指定受控制序列的結尾。|  
|[map::equal_range (STL/CLR)](#equal_range)|尋找符合指定之索引鍵的範圍。|  
|[map::erase (STL/CLR)](#erase)|移除位於指定位置的項目。|  
|[map::find (STL/CLR)](#find)|尋找符合指定之索引鍵的元素。|  
|[map::insert (STL/CLR)](#insert)|加入項目。|  
|[map::key_comp (STL/CLR)](#key_comp)|複製兩個索引鍵的排序委派。|  
|[map::lower_bound (STL/CLR)](#lower_bound)|尋找符合指定的索引鍵的範圍開頭。|  
|[map::make_value (STL/CLR)](#make_value)|建構值物件。|  
|[map::map (STL/CLR)](#map)|建構容器物件。|  
|[map::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|  
|[map::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|  
|[map::size (STL/CLR)](#size)|計算元素的數目。|  
|[map::swap (STL/CLR)](#swap)|交換兩個容器的內容。|  
|[map::to_array (STL/CLR)](#to_array)|將受控制的序列複製到新的陣列。|  
|[map::upper_bound (STL/CLR)](#upper_bound)|尋找符合指定的索引鍵的範圍結尾。|  
|[map::value_comp (STL/CLR)](#value_comp)|複製兩個項目值的順序委派。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[map::operator= (STL/CLR)](#op_as)|取代受控制的序列。|  
|[map::operator (STL/CLR)](#op)|將索引鍵對應至其相關聯的對應值。|  
|[operator!= (map) (STL/CLR)](#op_neq)|決定是否`map`物件是否不等於另一個`map`物件。|  
|[operator< (map) (STL/CLR)](#op_lt)|決定是否`map`物件是否小於另一個`map`物件。|  
|[operator<= (map) (STL/CLR)](#op_lteq)|決定是否`map`物件是否小於或等於另一個`map`物件。|  
|[operator== (map) (STL/CLR)](#op_eq)|決定是否`map`物件是否等於另一個`map`物件。|  
|[operator> (map) (STL/CLR)](#op_gt)|決定是否`map`物件是否大於另一個`map`物件。|  
|[operator>= (map) (STL/CLR)](#op_gteq)|決定是否`map`物件是否大於或等於另一個`map`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|<xref:System.Collections.IEnumerable>|透過項目進行排序。|  
|<xref:System.Collections.ICollection>|維護項目群組。|  
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的項目進行排序。|  
|<xref:System.Collections.Generic.ICollection%601>|維護群組的具類型的項目。|  
|<xref:System.Collections.Generic.IDictionary%602>|維護群組 {索引鍵，值} 組。|  
|ITree < 索引鍵、 值 >|維護泛型容器。|  
  
## <a name="remarks"></a>備註  
 物件，配置並釋放它做為個別的節點所控制之序列的儲存體。 它會將元素插入 （幾乎） 平衡樹狀目錄中，它會保留已排序的變更不會將一個節點的內容複製到另一個節點之間的連結。 這表示您可以插入和移除自由而不會干擾其餘元素的項目。  
  
 物件會排列它所控制藉由呼叫預存的委派物件的型別序列[map:: key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)。 當您建構對應時，您可以指定預存的委派物件如果您指定沒有委派的物件時，預設值是比較`operator<(key_type, key_type)`。 您可以存取這個預存的物件藉由呼叫成員函式[map:: key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)`()`。  
  
 這類委派物件必須強制執行嚴格弱式排序索引鍵的型別[map:: key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)。 這表示任何兩個索引鍵`X`和`Y`:  
  
 `key_comp()(X, Y)` 傳回的結果相同的布林值，在每次呼叫。  
  
 如果`key_comp()(X, Y)`為 true，然後`key_comp()(Y, X)`必須為偽。  
  
 如果`key_comp()(X, Y)`為 true，然後`X`稱為排序之前`Y`。  
  
 如果`!key_comp()(X, Y) && !key_comp()(Y, X)`為 true，然後`X`和`Y`被視為具有對等順序。  
  
 對於任何項目`X`前面`Y`在受控制的序列，`key_comp()(Y, X)`為 false。 （預設委派物件的索引鍵永遠不會減少值中。）不同於樣板類別[地圖](../dotnet/map-stl-clr.md)，樣板類別的物件`map`不需要的所有元素的索引鍵是唯一。 （兩個或多個金鑰可包含對等順序）。  
  
 每個項目包含一個個別的索引鍵和對應的值。 序列的表示方式允許查閱、 插入和移除任意項目以數字的對數的項目數目成正比的作業順序 （也就是對數時間）。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。  
  
 對應支援雙向迭代器，這表示您可以逐步執行至相鄰的項目指定的 iterator 可指定受控制序列中的項目。 特殊的前端節點會對應至所傳回的迭代器[map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`。 如果有的話，您可以遞增到最後一個項目，在受控制序列中，此迭代器。 您可以遞增對應迭代器，連線到前端節點，並接著它會比較等於`end()`。 您無法取值 （dereference） 所傳回的迭代器，但`end()`。  
  
 請注意，您不能參考直接指定其數值位置-所需的隨機存取迭代器的對應項目。  
  
 對應的迭代器會儲存其相關聯的對應 節點，接著會儲存其相關聯的容器的控制代碼的控制代碼。 您可以使用迭代器，只能搭配其相關聯的容器物件。 只要其相關聯的網站導覽節點是與部分地圖相關聯的對應迭代器會保持有效。 此外，有效的迭代器取值--您可以使用它來存取或修改的項目值，它會指定-只要不等於`end()`。  
  
 清除或移除一個項目呼叫解構函式，其預存值。 終結容器清除所有項目。 因此，的容器，其項目類型是 ref 類別可確保任何項目必須有存在的容器。 不過請注意，容器的控制代碼，並會*不*終結其項目。  
  
## <a name="members"></a>成員

## <a name="begin"></a> map:: begin (STL/CLR)
指定受控制序列的開頭。  
  
### <a name="syntax"></a>語法  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回指定之受控制的序列，或只是超出空序列結尾的第一個元素的雙向迭代器。 您用它來取得 iterator，指定`current`如果受控制序列的長度變更，可以變更受控制的序列，但其狀態的開頭。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_begin.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mymap::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*++begin() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*begin() = [a 1]  
*++begin() = [b 2]  
```  

## <a name="clear"></a> map:: clear (STL/CLR)
移除所有項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void clear();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會有效地呼叫[map:: erase (STL/CLR)](../dotnet/map-erase-stl-clr.md) `(` [map:: begin (STL/CLR)](../dotnet/map-begin-stl-clr.md) `(),` [map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) `())`. 您可以使用它來確保受控制的序列是空白。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_clear.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
  
// display contents " [a 1] [b 2]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0  
 [a 1] [b 2]  
size() = 0  
```  

## <a name="const_iterator"></a> map:: const_iterator (STL/CLR)
用於受控制序列的常數迭代器類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定型別的物件`T2`，可做為受控制序列的常數雙向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_const_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" [{0} {1}]", cit->first, cit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="const_reference"></a> map:: const_reference (STL/CLR)
項目的常數參考類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述項目的常數參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_const_reference.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Mymap::const_reference cref = *cit;   
        System::Console::Write(" [{0} {1}]", cref->first, cref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="const_reverse_iterator"></a> map:: const_reverse_iterator (STL/CLR)
受控制序列的常數反向迭代器的型別...  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定型別的物件`T4`，可做為受控制序列的常數反向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Mymap::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" [{0} {1}]", crit->first, crit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  

## <a name="count"></a> map:: count (STL/CLR)
尋找符合指定索引鍵的項目數目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
size_type count(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 *key*  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 此成員函式具有相同的順序，與受控制序列中傳回的項目數*金鑰*。 您可以使用它來判斷目前在受控制序列中符合指定之索引鍵的項目數目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_count.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  

## <a name="difference_type"></a> map:: difference_type (STL/CLR)
兩個項目之間帶正負號距離的類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述可能是負數的項目計數。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_difference_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mymap::difference_type diff = 0;   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Mymap::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> map:: empty (STL/CLR)
測試項目是否不存在。  
  
### <a name="syntax"></a>語法  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會對空的受控制序列傳回 true。 它相當於[map:: size (STL/CLR)](../dotnet/map-size-stl-clr.md)`() == 0`。 您可以使用它來測試是否是空的對應。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_empty.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="end"></a> map:: end (STL/CLR)
指定受控制序列的結尾。  
  
### <a name="syntax"></a>語法  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回雙向迭代器指向超過受控制序列的結尾。 您用它來取得 iterator，指定受控制序列中，結尾其狀態不變更如果受控制序列的長度變更。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_end.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Mymap::iterator it = c1.end();   
    --it;   
    --it;   
    System::Console::WriteLine("*-- --end() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*--end() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
```  

## <a name="equal_range"></a> map:: equal_range (STL/CLR)
尋找符合指定之索引鍵的範圍。  
  
### <a name="syntax"></a>語法  
  
```cpp  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 *key*  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回一組迭代器`cliext::pair<iterator, iterator>(` [map:: lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md) `(key),` [map:: upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)`(key))`。 您可以使用它來判斷目前在受控制序列中符合指定之索引鍵的項目範圍。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_equal_range.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_iter Pairii;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" [{0} {1}]",   
            pair1.first->first, pair1.first->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
equal_range(L'x') empty = True  
 [b 2]  
```  
  
## <a name="erase"></a> map:: erase (STL/CLR)
移除位於指定位置的項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### <a name="parameters"></a>參數  
 *first*  
 若要清除的範圍的開頭。  
  
 *key*  
 若要清除的機碼值。  
  
 *最後一個*  
 若要清除的範圍的結尾。  
  
 *where*  
 若要清除的項目。  
  
### <a name="remarks"></a>備註  
 第一個成員函式會移除所指向之受控制序列的項目*何處*，並傳回指定移除的項目之外剩餘的第一個元素的迭代器或[map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md) `()`如果沒有這類項目。 您可以使用它來移除單一項目。  
  
 第二個成員函式範圍中移除受控制序列的項目 [`first`， `last`)，並傳回指定任何移除的項目之外剩餘的第一個元素的迭代器或`end()`如果沒有這類項目存在... 您可以使用它來移除零或多個連續的項目。  
  
 第三個成員函式中移除索引鍵具有對等排序受控制任何的序列項目來*金鑰*，並傳回已移除的元素數目計數。 您可以使用它來移除，並計算所有符合指定之索引鍵的項目。  
  
 每個項目清除會花在受控制序列中的項目數目對數值成比例的時間。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_erase.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    cliext::map<wchar_t, int> c1;   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'a', 1));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'b', 2));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (cliext::map<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    cliext::map<wchar_t, int>::iterator it =   
        c1.erase(c1.begin());   
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",   
        it->first, it->second);   
  
// add elements and display " b c d e"   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'd', 4));   
    c1.insert(cliext::map<wchar_t, int>::make_value(L'e', 5));   
    for each (cliext::map<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase all but end   
    it = c1.end();   
    it = c1.erase(c1.begin(), --it);   
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",   
        it->first, it->second);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// erase end   
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));   
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
erase(begin()) = [b 2]  
 [b 2] [c 3] [d 4] [e 5]  
erase(begin(), end()-1) = [e 5]  
size() = 1  
erase(L'x') = 0  
erase(L'e') = 1  
```  
  
## <a name="find"></a> map:: find (STL/CLR)
尋找符合指定之索引鍵的元素。  
  
### <a name="syntax"></a>語法  
  
```cpp  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 *key*  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 如果受控制序列中的至少一個項目具有與對等順序*金鑰*，此成員函式會傳回迭代器指定其中一個項目; 否則會傳回[map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. 您可以使用它來尋找符合指定的索引鍵之受控制序列中目前的元素。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_find.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
  
    Mymap::iterator it = c1.find(L'b');   
    System::Console::WriteLine("find {0} = [{1} {2}]",   
        L'b', it->first, it->second);   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
find A = False  
find b = [b 2]  
find C = False  
```  

## <a name="generic_container"></a> map::generic_container (STL/CLR)
容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::  
    ITree<GKey, GValue>  
    generic_container;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述此範本的容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_generic_container.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(Mymap::make_value(L'd', 4));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(Mymap::make_value(L'e', 5));   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3] [d 4]  
[a 1] [b 2] [c 3] [d 4] [e 5]  
```  

## <a name="generic_iterator"></a> map::generic_iterator (STL/CLR)
迭代器，用於容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述可以搭配此範本的容器類別的泛型介面的泛型迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymap::generic_iterator gcit = gc1->begin();   
    Mymap::generic_value gcval = *gcit;   
    System::Console::Write(" [{0} {1}]", gcval->first, gcval->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1]  
```  

## <a name="generic_reverse_iterator"></a> map::generic_reverse_iterator (STL/CLR)
反向迭代器，用於容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述的一般反向迭代器可以搭配此範本的容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymap::generic_reverse_iterator gcit = gc1->rbegin();   
    Mymap::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[c 3]  
```  

## <a name="generic_value"></a> map::generic_value (STL/CLR)
使用容器的泛型介面的項目型別。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>備註  
 此類型所描述型別的物件`GValue`，描述與此範本的容器類別的泛型介面使用的預存的項目值。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_generic_value.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymap::generic_container^ gc1 = %c1;   
    for each (Mymap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymap::generic_iterator gcit = gc1->begin();   
    Mymap::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1]  
```  

## <a name="insert"></a> map:: insert (STL/CLR)
加入項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
cliext::pair<iterator, bool> insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 *first*  
 若要插入的範圍的開頭。  
  
 *最後一個*  
 若要插入的範圍的結尾。  
  
 *right*  
 若要插入的列舉型別。  
  
 *val*  
 要插入的關鍵值。  
  
 *where*  
 若要插入 （只提示） 的容器中的位置。  
  
### <a name="remarks"></a>備註  
 每個成員函式會插入為其餘運算元所指定的順序。  
  
 第一個成員函式會嘗試插入具有值的項目*val*，並傳回一組值`X`。 如果`X.second`為 true，`X.first`指定新插入的項目，否則為`X.first`指定具有對等項目排序已存在，且會插入任何新的項目。 您可以使用它來插入單一項目。  
  
 第二個成員函式會插入具有值的項目*val*，並使用*其中*做為提示 （若要改善效能），並傳回迭代器，指定新插入的項目。 您可以使用它來插入單一項目可能是您知道的項目旁。  
  
 第三個成員函式會插入序列 [`first`， `last`)。 您可以使用它來插入另一個序列中複製的零或多個項目。  
  
 第四個成員函式會插入所指定的順序*右*。 您可以使用它來插入列舉值所描述的順序。  
  
 每個項目插入受控制序列中需要的項目數目對數值成比例的時間。 插入可能會發生在平攤常數時間，不過，提供指定的項目旁的插入點的提示。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_insert.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef Mymap::pair_iter_bool Pairib;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
// insert a single value, success and failure   
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    pair1 = c1.insert(Mymap::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    Mymap::iterator it =   
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymap c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymap c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Mymap::value_type>^)%c1);   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
insert([L'x' 24]) = [[x 24] True]  
insert([L'b' 2]) = [[b 2] False]  
 [a 1] [b 2] [c 3] [x 24]  
insert(begin(), [L'y' 25]) = [y 25]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
 [a 1] [b 2] [c 3] [x 24]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
```  

## <a name="iterator"></a> map:: iterator (STL/CLR)
受控制序列之迭代器的類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定型別的物件`T1`，可做為受控制序列的雙向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" [{0} {1}]", it->first, it->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  

## <a name="key_comp"></a> map:: key_comp (STL/CLR)
複製兩個索引鍵的排序委派。  
  
### <a name="syntax"></a>語法  
  
```cpp  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回用來排序受控制的序列的順序委派。 您可以使用它來比較兩個索引鍵。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_key_comp.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymap c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_compare"></a> map:: key_compare (STL/CLR)
兩個索引鍵排序委派。  
  
### <a name="syntax"></a>語法  
  
```cpp  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
### <a name="remarks"></a>備註  
 此類型為委派，來決定其索引鍵的引數的順序的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_key_compare.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymap c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```

## <a name="key_type"></a> map:: key_type (STL/CLR)
排序索引鍵的類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>備註  
 類型是範本參數的同義字*金鑰*。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_key_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using key_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Mymap::key_type val = it->first;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="lower_bound"></a> map:: lower_bound (STL/CLR)
尋找符合指定的索引鍵的範圍開頭。  
  
### <a name="syntax"></a>語法  
  
```cpp  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 *key*  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 判斷第一個項目成員函式`X`相等排序受控制序列中*金鑰*。 如果沒有這類元素存在，它會傳回[map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; 否則會傳回迭代器指定`X`。 您可以使用它來在受控制序列中符合指定之索引鍵中目前找出的項目序列的開頭。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_lower_bound.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Mymap::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = [a 1]  
*lower_bound(L'b') = [b 2]  
```  

## <a name="make_value"></a> map::make_value (STL/CLR)
建構值物件。  
  
### <a name="syntax"></a>語法  
  
```cpp  
static value_type make_value(key_type key, mapped_type mapped);  
```  
  
#### <a name="parameters"></a>參數  
 *key*  
 若要使用的金鑰值。  
  
 *對應*  
 要搜尋的對應的值。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回`value_type`其索引鍵的物件*金鑰*和其對應的值是*對應*。 您可以使用它來撰寫適用於數個其他成員函式物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_make_value.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="map"></a> map:: map (STL/CLR)
建構容器物件。  
  
### <a name="syntax"></a>語法  
  
```cpp  
map();  
explicit map(key_compare^ pred);  
map(map<Key, Mapped>% right);  
map(map<Key, Mapped>^ right);  
template<typename InIter>  
    mapmap(InIter first, InIter last);  
template<typename InIter>  
    map(InIter first, InIter last,  
        key_compare^ pred);  
map(System::Collections::Generic::IEnumerable<GValue>^ right);  
map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>參數  
 *first*  
 若要插入的範圍的開頭。  
  
 *最後一個*  
 若要插入的範圍的結尾。  
  
 *預測*  
 排序受控制序列的述詞。  
  
 *right*  
 要插入的物件或範圍。  
  
### <a name="remarks"></a>備註  
 建構函式：  
  
 `map();`  
  
 排序的述詞的預設值，初始化受控制的序列的任何項目， `key_compare()`。 您可以使用它來指定空的初始受控制的序列，以預設的排序的述詞。  
  
 建構函式：  
  
 `explicit map(key_compare^ pred);`  
  
 初始化受控制的序列沒有項目時，使用 排序的述詞*pred*。 您可以使用它來指定空的初始受控制的序列，指定排序的述詞。  
  
 建構函式：  
  
 `map(map<Key, Mapped>% right);`  
  
 初始化受控制的序列具有序列 [`right.begin()`， `right.end()`)，排序的述詞的預設值。 您使用它來指定初始受控制的序列的 map 物件所控制之序列的複本*右*，排序的述詞的預設值。  
  
 建構函式：  
  
 `map(map<Key, Mapped>^ right);`  
  
 初始化受控制的序列具有序列 [`right->begin()`， `right->end()`)，排序的述詞的預設值。 您使用它來指定初始受控制的序列的 map 物件所控制之序列的複本*右*，排序的述詞的預設值。  
  
 建構函式：  
  
 `template<typename InIter> map(InIter first, InIter last);`  
  
 初始化受控制的序列具有序列 [`first`， `last`)，排序的述詞的預設值。 您可以使用它來建立受控制的序列的設定，一份另一個的順序，排序的述詞的預設值。  
  
 建構函式：  
  
 `template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控制的序列具有序列 [`first`， `last`)，以排序的述詞*pred*。 您可以使用它來建立一份具有指定排序的述詞的另一個序列的受控制的序列。  
  
 建構函式：  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序*右*，排序的述詞的預設值。 您可以使用它來進行受控制的序列的列舉值，描述排序的述詞的預設值的另一個序列的複本。  
  
 建構函式：  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化受控制的序列的列舉值所指定的順序*右*，以排序的述詞*pred*。 您可以使用它來進行受控制的序列的列舉值，指定排序的述詞所描述的另一個序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
// construct an empty container   
    Mymap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymap c3(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3);   
    for each (Mymap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymap c7(c4);   
    for each (Mymap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymap c8(%c3);   
    for each (Mymap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
```  

## <a name="mapped_type"></a> map:: mapped_type (STL/CLR)
與每個索引鍵關聯的對應值類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef Mapped mapped_type;  
```  
  
### <a name="remarks"></a>備註  
 類型是範本參數的同義字*對應*。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_mapped_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using mapped_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in mapped_type object   
        Mymap::mapped_type val = it->second;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
1 2 3  
```  
  
## <a name="op_as"></a> map:: operator = (STL/CLR)
取代受控制的序列。  
  
### <a name="syntax"></a>語法  
  
```cpp  
map<Key, Mapped>% operator=(map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *right*  
 要複製的容器。  
  
### <a name="remarks"></a>備註  
 成員運算子複製*右*物件，然後傳回`*this`。 您使用它來取代受控制的序列中的受控制序列的複本*右*。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_operator_as.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2 = c1;   
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
```  

## <a name="op"></a> map::operator(STL/CLR)
將索引鍵對應至其相關聯的對應值。  
  
### <a name="syntax"></a>語法  
  
```cpp  
mapped_type operator[](key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 *key*  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 此成員函式以尋找具有相等排序的元素的初衷*金鑰*。 如果找到，它會傳回相關聯的對應的值。否則，它會插入`value_type(key, mapped_type())`，並傳回相關聯 （預設值） 的對應值。 您使用它來查閱對應的值，指定其相關聯的索引鍵，或如果找不到索引鍵存在的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_operator_sub.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'A', c1[L'A']);   
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'b', c1[L'b']);   
  
// redisplay altered contents   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// alter mapped values and redisplay   
    c1[L'A'] = 10;   
    c1[L'c'] = 13;   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
c1[A] = 0  
c1[b] = 2  
 [A 0] [a 1] [b 2] [c 3]  
 [A 10] [a 1] [b 2] [c 13]  
```  

## <a name="rbegin"></a> map:: rbegin (STL/CLR)
指定反向受控制序列的開頭。  
  
### <a name="syntax"></a>語法  
  
```cpp  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回指定之受控制的序列，或只是超出空序列開頭的最後一個元素的反向迭代器。 因此，它會指定`beginning`反向序列。 您用它來取得 iterator，指定`current`如果受控制序列的長度變更，可以變更以反向順序顯示之受控制的序列，但其狀態的開頭。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_rbegin.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymap::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*rbegin() = [c 3]  
*++rbegin() = [b 2]  
```  

## <a name="reference"></a> map:: reference (STL/CLR)
項目的參考類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述項目的參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_reference.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Mymap::reference ref = *it;   
        System::Console::Write(" [{0} {1}]", ref->first, ref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
``` 

## <a name="rend"></a> map:: rend (STL/CLR)
指定反向受控制序列的結尾。  
  
### <a name="syntax"></a>語法  
  
```cpp  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式傳回的反向迭代器指向之外開頭之受控制序列。 因此，它會指定`end`反向序列。 您用它來取得 iterator，指定`current`如果受控制序列的長度變更，可以變更結尾以反向順序顯示之受控制的序列，但其狀態。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_rend.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymap::reverse_iterator rit = c1.rend();   
    --rit;   
    --rit;   
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*--rend() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*-- --rend() = [b 2]  
*--rend() = [a 1]  
```   

## <a name="reverse_iterator"></a> map:: reverse_iterator (STL/CLR)
受控制序列的反向迭代器類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Mymap::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" [{0} {1}]", rit->first, rit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  

## <a name="size"></a> map:: size (STL/CLR)
計算元素的數目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列的項目數。 如果您在意順序是否有非零值的大小，請參閱[map:: empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)`()`。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_size.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(Mymap::make_value(L'd', 4));   
    c1.insert(Mymap::make_value(L'e', 5));   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0 after clearing  
size() = 2 after adding 2  
```  

## <a name="size_type"></a> map:: size_type (STL/CLR)
兩個項目之間帶正負號距離的類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述的非負數的項目計數。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_size_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mymap::size_type diff = 0;   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
end()-begin() = 3  
```  
  
## <a name="swap"></a> map:: swap (STL/CLR)
交換兩個容器的內容。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void swap(map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *right*  
 要交換內容的容器。  
  
### <a name="remarks"></a>備註  
 此成員函式會交換之間受控制的序列`this`並*右*。 它會以常數時間，就會擲回任何例外狀況。 您可以使用它作為兩個容器的內容交換的快速方法。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_swap.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'd', 4));   
    c2.insert(Mymap::make_value(L'e', 5));   
    c2.insert(Mymap::make_value(L'f', 6));   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[d 4] [e 5] [f 6]  
[d 4] [e 5] [f 6]  
[a 1] [b 2] [c 3]  
```  

## <a name="to_array"></a> map::to_array (STL/CLR)
將受控制的序列複製到新的陣列。  
  
### <a name="syntax"></a>語法  
  
```cpp  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回包含之受控制的序列的陣列。 您可以使用它來取得陣列形式中受控制序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_to_array.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// copy the container and modify it   
    cli::array<Mymap::value_type>^ a1 = c1.to_array();   
  
    c1.insert(Mymap::make_value(L'd', 4));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (Mymap::value_type elem in a1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
[a 1] [b 2] [c 3] [d 4]  
[a 1] [b 2] [c 3]  
```  

## <a name="upper_bound"></a> map:: upper_bound (STL/CLR)
尋找符合指定的索引鍵的範圍結尾。  
  
### <a name="syntax"></a>語法  
  
```cpp  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 *key*  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 此成員函式決定最後一個項目`X`相等排序受控制序列中*金鑰*。 如果沒有這類元素存在，或如果`X`是最後一個項目，在受控制的序列，它會傳回[map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; 否則會傳回迭代器，指定第一個項目超過`X`. 您可以使用它來在受控制序列中符合指定之索引鍵中目前找出的項目序列的結尾。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_upper_bound.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Mymap::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = [b 2]  
*upper_bound(L'b') = [c 3]  
```  

## <a name="value_comp"></a> map:: value_comp (STL/CLR)
複製兩個項目值的順序委派。  
  
### <a name="syntax"></a>語法  
  
```cpp  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回用來排序受控制的序列的順序委派。 您可以使用它來比較兩個項目值。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_value_comp.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'b', 2),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
compare([L'a', 1], [L'a', 1]) = False  
compare([L'a', 1], [L'b', 2]) = True  
compare([L'b', 2], [L'a', 1]) = False  
```  
  
## <a name="value_compare"></a> map::value_compare (STL/CLR)
兩個元素值排序委派。  
  
### <a name="syntax"></a>語法  
  
```cpp  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
### <a name="remarks"></a>備註  
 此類型為委派，來決定其值引數的順序的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_value_compare.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'b', 2),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
compare([L'a', 1], [L'a', 1]) = False  
compare([L'a', 1], [L'b', 2]) = True  
compare([L'b', 2], [L'a', 1]) = False  
```  

## <a name="value_type"></a> map:: value_type (STL/CLR)
元素的類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef generic_value value_type;  
```  
  
### <a name="remarks"></a>備註  
 這個類型與 `generic_value`同義。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_value_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using value_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mymap::value_type val = *it;   
        System::Console::Write(" [{0} {1}]", val->first, val->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="op_neq"></a> 運算子 ！ = (map) (STL/CLR)
列出不相等比較。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator!=(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(left == right)`。 您會使用它來測試是否*左*未經過排序相同*右*當兩個對應都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_operator_ne.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  
  
## <a name="op_lt"></a> 運算子&lt;(map) (STL/CLR)
清單小於比較。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator<(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式傳回則為 true，最低的位置`i`為其`!(right[i] < left[i])`也雖說， `left[i] < right[i]`。 否則，它會傳回`left->size() < right->size()`使用它來測試是否*左*排序之前*右*當兩個對應都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_operator_lt.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> 運算子&lt;= (map) (STL/CLR)
清單小於或等於比較。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator<=(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(right < left)`。 您會使用它來測試是否*左*未經過排序之後*右*當兩個對應都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_operator_le.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  

## <a name="op_eq"></a> 運算子 = = (map) (STL/CLR)
列出相等比較。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator==(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回 true 所控制的序列時，才*左*並*右*具有相同的長度和每個位置`i`， `left[i] ==` `right[i]`。 您會使用它來測試是否*左*排序相同*右*當兩個對應都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_operator_eq.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  

## <a name="op_gt"></a> 運算子&gt;(map) (STL/CLR)
大於比較的清單。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator>(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`right` `<` `left`。 您會使用它來測試是否*左*經過排序之後*右*當兩個對應都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_operator_gt.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  

## <a name="op_gteq"></a> 運算子&gt;= (map) (STL/CLR)
清單大於或等於比較。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Key,  
    typename Mapped>  
    bool operator>=(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(left` `<` `right)`。 您會使用它來測試是否*左*未經過排序再*右*當兩個對應都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_map_operator_ge.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
``` 