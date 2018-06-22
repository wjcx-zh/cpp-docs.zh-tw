---
title: 設定 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::set::begin
- cliext::set::clear
- cliext::set::const_iterator
- cliext::set::const_reference
- cliext::set::const_reverse_iterator
- cliext::set::count
- cliext::set::difference_type
- cliext::set::empty
- cliext::set::end
- cliext::set::equal_range
- cliext::set::erase
- cliext::set::find
- cliext::set::generic_container
- cliext::set::generic_iterator
- cliext::set::generic_reverse_iterator
- cliext::set::generic_value
- cliext::set::insert
- cliext::set::iterator
- cliext::set::key_comp
- cliext::set::key_compare
- cliext::set::key_type
- cliext::set::lower_bound
- cliext::set::make_value
- cliext::set::operator=
- cliext::set::rbegin
- cliext::set::reference
- cliext::set::rend
- cliext::set::reverse_iterator
- cliext::set::set
- cliext::set::size
- cliext::set::size_type
- cliext::set::swap
- cliext::set::to_array
- cliext::set::upper_bound
- cliext::set::value_comp
- cliext::set::value_compare
- cliext::set::value_type
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
- operator!= (set) member [STL/CLR]
- operator< (set) member [STL/CLR]
- operator<= (set) member [STL/CLR]
- operator== (set) member [STL/CLR]
- operator> (set) member [STL/CLR]
- operator>= (set) member [STL/CLR]
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
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- set member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 99ea41a77a8ed01cb78df3513ccb79b6b2a8b3f1
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305887"
---
# <a name="set-stlclr"></a>set (STL/CLR)
此範本類別描述控制不同長度序列的項目具有雙向存取的物件。 使用容器`set`管理項目序列 （幾乎） 平衡排序樹狀結構的節點，各儲存一個項目。  
  
 在以下描述`GValue`相同`GKey`，這又是相同`Key`後者是 ref 型別，除非在這種情況下很`Key^`。  
  
### <a name="syntax"></a>語法  
  
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
  
## <a name="declarations"></a>宣告  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[set::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|  
|[set::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|  
|[set::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|  
|[set::difference_type (STL/CLR)](#difference_type)|兩個項目之間的 （可能是帶正負號） 距離的類型。|  
|[set::generic_container (STL/CLR)](#generic_container)|容器的泛型介面型別。|  
|[set::generic_iterator (STL/CLR)](#generic_iterator)|泛型介面，該容器的迭代器類型。|  
|[set::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面的反向迭代器類型。|  
|[set::generic_value (STL/CLR)](#generic_value)|泛型介面的容器項目的類型。|  
|[set::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|  
|[set::key_compare (STL/CLR)](#key_compare)|兩個索引鍵排序的委派。|  
|[set::key_type (STL/CLR)](#key_type)|排序索引鍵的類型。|  
|[set::reference (STL/CLR)](#reference)|項目的參考類型。|  
|[set::reverse_iterator (STL/CLR)](#reverse_iterator)|受控制序列的反向迭代器類型。|  
|[set::size_type (STL/CLR)](#size_type)|（非負數） 之間的距離的兩個項目類型。|  
|[set::value_compare (STL/CLR)](#value_compare)|兩個項目值順序的委派。|  
|[set::value_type (STL/CLR)](#value_type)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[set::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|  
|[set::clear (STL/CLR)](#clear)|移除所有項目。|  
|[set::count (STL/CLR)](#count)|計算指定的索引鍵相符的項目。|  
|[set::empty (STL/CLR)](#empty)|測試項目是否不存在。|  
|[set::end (STL/CLR)](#end)|指定受控制序列的結尾。|  
|[set::equal_range (STL/CLR)](#equal_range)|尋找符合指定之索引鍵的範圍。|  
|[set::erase (STL/CLR)](#erase)|移除位於指定位置的項目。|  
|[set::find (STL/CLR)](#find)|尋找符合指定之索引鍵的元素。|  
|[set::insert (STL/CLR)](#insert)|加入項目。|  
|[set::key_comp (STL/CLR)](#key_comp)|將複製兩個索引鍵的順序委派。|  
|[set::lower_bound (STL/CLR)](#lower_bound)|尋找符合指定之索引鍵的範圍開頭。|  
|[set::make_value (STL/CLR)](#make_value)|建構值物件。|  
|[set::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|  
|[set::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|  
|[set::set (STL/CLR)](#set)|建構容器物件。|  
|[set::size (STL/CLR)](#size)|計算元素的數目。|  
|[set::swap (STL/CLR)](#swap)|交換兩個容器的內容。|  
|[set::to_array (STL/CLR)](#to_array)|將受控制的序列複製到新的陣列。|  
|[set::upper_bound (STL/CLR)](#upper_bound)|尋找符合指定之索引鍵的範圍結尾。|  
|[set::value_comp (STL/CLR)](#value_comp)|將複製兩個項目值的順序委派。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[set::operator= (STL/CLR)](#op_as)|取代受控制的序列。|  
|[operator!= (set) (STL/CLR)](#op_neq)|決定如果`set`物件是否不等於另一個`set`物件。|  
|[operator< (set) (STL/CLR)](#op_lt)|決定如果`set`物件是否小於另一個`set`物件。|  
|[operator<= (set) (STL/CLR)](#op_lteq)|決定如果`set`物件是否小於或等於另一個`set`物件。|  
|[operator== (set) (STL/CLR)](#op_eq)|決定如果`set`物件是否等於另一個`set`物件。|  
|[operator> (set) (STL/CLR)](#op_gt)|決定如果`set`物件是否大於另一個`set`物件。|  
|[operator>= (set) (STL/CLR)](#op_gteq)|決定如果`set`物件是否大於或等於另一個`set`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|<xref:System.Collections.IEnumerable>|項目順序。|  
|<xref:System.Collections.ICollection>|維護群組的項目。|  
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的項目順序。|  
|<xref:System.Collections.Generic.ICollection%601>|維護群組的具類型的項目。|  
|ITree\<索引鍵、 值 >|維護泛型容器。|  
  
### <a name="remarks"></a>備註  
 物件可配置及釋放它做為個別的節點所控制的序列的儲存體。 它會將元素插入 （幾乎） 平衡樹狀目錄中，它會保留排序會改變節點，而非由複製到另一個節點的內容之間的連結。 這表示您可以插入和移除項目，自由地不干擾其餘項目。  
  
 物件，排序它藉由呼叫預存的委派類型的物件所控制的序列[set:: key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)。 當您建構組; 時，您可以指定預存的委派物件如果您指定沒有委派的物件時，預設值是比較`operator<(key_type, key_type)`。 您藉由呼叫成員函式中存取這個預存的物件[set:: key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`。  
  
 這類委派的物件必須強制執行嚴格弱式排序索引鍵的型別[set:: key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)。 這表示任何兩個索引鍵`X`和`Y`:  
  
 `key_comp()(X, Y)` 傳回的相同的布林值結果，在每次呼叫。  
  
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
 
## <a name="members"></a>成員

## <a name="begin"></a>set:: begin (STL/CLR)
指定受控制序列的開頭。  
  
### <a name="syntax"></a>語法  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回指定的受控制序列中，或空序列結尾之外的第一個元素的雙向迭代器。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更受控制的序列中，但其狀態的開頭。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_begin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myset::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  

## <a name="clear"></a>set:: clear (STL/CLR)
移除所有項目。  
  
### <a name="syntax"></a>語法  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>備註  
 成員函式可有效地呼叫[set:: erase (STL/CLR)](../dotnet/set-erase-stl-clr.md) `(` [set:: begin (STL/CLR)](../dotnet/set-begin-stl-clr.md) `(),` [set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md) `())`. 您可以使用它來確定受控制的序列是空白。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_clear.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  

## <a name="const_iterator"></a>set:: const_iterator (STL/CLR)
用於受控制序列的常數迭代器類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T2`，可做為受控制序列的常數的雙向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_const_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a>set:: const_reference (STL/CLR)
項目的常數參考類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述項目的常數參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_const_reference.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Myset::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a>set:: const_reverse_iterator (STL/CLR)
受控制序列的常數反向迭代器型別...  
  
### <a name="syntax"></a>語法  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T4`，可做為受控制序列的常數反向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="count"></a>set:: count (STL/CLR)
尋找符合指定索引鍵的項目數目。  
  
### <a name="syntax"></a>語法  
  
```  
size_type count(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 成員函式具有對等順序，與受控制序列中傳回的項目數`key`。 您可以使用它來判斷目前在受控制序列中符合指定之索引鍵的項目數目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_count.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  

## <a name="difference_type"></a>set:: difference_type (STL/CLR)
兩個項目之間的帶正負號距離的類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述負可能是項目計數。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_difference_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myset::difference_type diff = 0;   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Myset::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a>set:: empty (STL/CLR)
測試項目是否不存在。  
  
### <a name="syntax"></a>語法  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會對空的受控制序列傳回 true。 它相當於[set:: size (STL/CLR)](../dotnet/set-size-stl-clr.md)`() == 0`。 您可以使用它來測試集合是否為空白。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_empty.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
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
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="end"></a>set:: end (STL/CLR)
指定受控制序列的結尾。  
  
### <a name="syntax"></a>語法  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回雙向迭代器，指向受控制序列的結尾之外。 您使用它來取得指定受控制序列的結尾的迭代器其狀態不改變受控制序列的長度變更時。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_end.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myset::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
```  

## <a name="equal_range"></a>set:: equal_range (STL/CLR)
尋找符合指定之索引鍵的範圍。  
  
### <a name="syntax"></a>語法  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回迭代器的一組`cliext::pair<iterator, iterator>(` [set:: lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md) `(key),` [set:: upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)`(key))`。 您可以使用它來判斷目前在受控制序列中符合指定之索引鍵的項目範圍。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_equal_range.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
typedef Myset::pair_iter_iter Pairii;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" {0}", *pair1.first);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
equal_range(L'x') empty = True  
 b  
``` 

## <a name="erase"></a>set:: erase (STL/CLR)
移除位於指定位置的項目。  
  
### <a name="syntax"></a>語法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
size_type erase(key_type key)  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 要清除範圍的開頭。  
  
 key  
 若要清除的機碼值。  
  
 last  
 若要清除的範圍的結尾。  
  
 其中  
 若要清除的項目。  
  
### <a name="remarks"></a>備註  
 第一個成員函式中移除指向受控制序列的項目`where`，並傳回指定移除的項目之外剩餘的第一個元素的迭代器或[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md) `()`如果沒有這類元素存在。 您可以使用它來移除單一項目。  
  
 第二個成員函式範圍中移除受控制序列的項目 [`first`， `last`)，並傳回指定任何移除的項目之外剩餘的第一個元素的迭代器或`end()`如果沒有這個項目存在... 您可以使用它來移除零或多個連續的項目。  
  
 第三個成員函式中移除索引鍵具有對等順序受控制任何的序列項目至`key`，並傳回已移除項目的數目的計數。 您可以使用它來移除並計算所有符合指定之索引鍵的項目。  
  
 每個項目清除接受受控制序列的項目數目對數值成比例的時間。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_erase.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```   

## <a name="find"></a>set:: find (STL/CLR)
尋找符合指定之索引鍵的元素。  
  
### <a name="syntax"></a>語法  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 受控制序列中的至少一個項目是否具有對等順序`key`，成員函式會傳回指定其中一個這些項目的迭代器，否則它會傳回[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`。 您可以使用它來尋找元素目前受控制序列之符合指定之索引鍵。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_find.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
    System::Console::WriteLine("find {0} = {1}",   
        L'b', *c1.find(L'b'));   
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
find A = False  
find b = b  
find C = False  
```  

## <a name="generic_container"></a>set::generic_container (STL/CLR)
容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```  
typedef Microsoft::VisualC::StlClr::  
    ITree<GKey, GValue>  
    generic_container;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述此樣板容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_generic_container.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(L'e');   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c d  
a b c d e  
```  
  
## <a name="generic_iterator"></a> set::generic_iterator (STL/CLR)
迭代器使用容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型所描述泛型的迭代器，可以搭配這個範本容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myset::generic_iterator gcit = gc1->begin();   
    Myset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```  
  
## <a name="generic_reverse_iterator"></a> set::generic_reverse_iterator (STL/CLR)
反向迭代器使用容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型所描述泛型反向迭代器，可以搭配這個範本容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myset::generic_reverse_iterator gcit = gc1->rbegin();   
    Myset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
c  
```  

## <a name="generic_value"></a> set::generic_value (STL/CLR)
使用容器的泛型介面的項目類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>備註  
 此類型所描述型別的物件`GValue`描述使用的預存的項目值與此範本容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_generic_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myset::generic_iterator gcit = gc1->begin();   
    Myset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```  
  
## <a name="insert"></a> set:: insert (STL/CLR)
加入項目。  
  
### <a name="syntax"></a>語法  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 向右  
 若要插入的列舉型別。  
  
 val  
 要插入索引鍵的值。  
  
 其中  
 若要插入 （只有提示） 的容器中的位置。  
  
### <a name="remarks"></a>備註  
 每個成員函式插入其餘運算元所指定的順序。  
  
 第一個成員函式插入具有值的項目儘量`val`，並傳回一組值`X`。 如果`X.second`為 true，`X.first`指定新插入的項目，否則為`X.first`指定對等項目與項目排序已存在，且會插入任何新元素。 您可以使用它來插入單一項目。  
  
 第二個成員函式插入值的項目`val`，並使用`where`做為提示 （若要改善效能），並傳回指定的新插入的元素的迭代器。 您可以使用它來插入這可能是您知道的項目旁的單一項目。  
  
 第三個成員函式會插入序列 [`first`， `last`)。 您可以使用它來插入其他順序從複製的零或多個項目。  
  
 第四個成員函式會插入所指定的序列`right`。 您可以使用它來插入列舉所描述的順序。  
  
 每個項目插入將會受控制序列中的項目數目對數值成比例的時間。 可能會插入在平攤常數時間，不過，給定的指定項目插入點至相鄰的提示。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
typedef Myset::pair_iter_bool Pairib;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Pairib pair1 = c1.insert(L'x');   
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    pair1 = c1.insert(L'b');   
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myset c2;   
    Myset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(L'x') = [x True]  
insert(L'b') = [b False]  
 a b c x  
insert(begin(), L'y') = y  
 a b c x y  
 a b c x  
 a b c x y  
```  

## <a name="iterator"></a> set:: iterator (STL/CLR)
受控制序列之迭代器的類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T1`，可做為受控制序列的雙向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="key_comp"></a> set:: key_comp (STL/CLR)
將複製兩個索引鍵的順序委派。  
  
### <a name="syntax"></a>語法  
  
```  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回用來排序受控制的序列的順序委派。 您可以使用它來比較兩個索引鍵。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_key_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myset c2 = cliext::greater<wchar_t>();   
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

## <a name="key_compare"></a> set:: key_compare (STL/CLR)
兩個索引鍵排序的委派。  
  
### <a name="syntax"></a>語法  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
### <a name="remarks"></a>備註  
 類型是同義字，以決定排序索引鍵引數的委派。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_key_compare.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myset c2 = cliext::greater<wchar_t>();   
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

## <a name="key_type"></a> set:: key_type (STL/CLR)
排序索引鍵的類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Key`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_key_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using key_type   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myset::key_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="lower_bound"></a> set:: lower_bound (STL/CLR)
尋找符合指定之索引鍵的範圍開頭。  
  
### <a name="syntax"></a>語法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 成員函式判斷第一個項目`X`具有對等順序，來控制序列中`key`。 如果沒有這類元素存在，它會傳回[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; 否則它會傳回迭代器，指定`X`。 您可以使用它來尋找項目序列的開頭目前受控制序列之符合指定之索引鍵。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_lower_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = a  
*lower_bound(L'b') = b  
```  

## <a name="make_value"></a> set::make_value (STL/CLR)
建構值物件。  
  
### <a name="syntax"></a>語法  
  
```  
static value_type make_value(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 若要使用的金鑰值。  
  
### <a name="remarks"></a>備註  
 成員函式傳回`value_type`物件的索引鍵是`key`。 您可以使用它來撰寫適用於數個其他成員函式物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_make_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(Myset::make_value(L'a'));   
    c1.insert(Myset::make_value(L'b'));   
    c1.insert(Myset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="op_as"></a> set::operator = (STL/CLR)
取代受控制的序列。  
  
### <a name="syntax"></a>語法  
  
```  
set<Key>% operator=(set<Key>% right);  
```  
  
#### <a name="parameters"></a>參數  
 向右  
 要複製的容器。  
  
### <a name="remarks"></a>備註  
 成員運算子複製`right`物件，然後傳回`*this`。 您使用它將受控制序列取代為 `right` 中受控制序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_operator_as.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="rbegin"></a> set:: rbegin (STL/CLR)
指定反向受控制序列的開頭。  
  
### <a name="syntax"></a>語法  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回指定受控制序列中，或空的序列開頭以外路徑的最後一個元素的反向迭代器。 因此，它會指定`beginning`反向序列。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更受控制的序列相反的順序出現，但其狀態的開頭。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_rbegin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myset::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
```  

## <a name="reference"></a> set:: reference (STL/CLR)
項目的參考類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述項目的參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_reference.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Myset::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```

## <a name="rend"></a> set:: rend (STL/CLR)
指定反向受控制序列的結尾。  
  
### <a name="syntax"></a>語法  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回以外的位置開始，指向受控制序列的反向迭代器。 因此，它會指定`end`反向序列。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更結尾受控制的序列相反的順序出現，但它的狀態。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_rend.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myset::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
```    

## <a name="reverse_iterator"></a> set:: reverse_iterator (STL/CLR)
受控制序列的反向迭代器類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="set"></a> set:: set (STL/CLR)
建構容器物件。  
  
### <a name="syntax"></a>語法  
  
```  
set();  
explicit set(key_compare^ pred);  
set(set<Key>% right);  
set(set<Key>^ right);  
template<typename InIter>  
    setset(InIter first, InIter last);  
template<typename InIter>  
    set(InIter first, InIter last,  
        key_compare^ pred);  
set(System::Collections::Generic::IEnumerable<GValue>^ right);  
set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 pred  
 排序受控制序列的述詞。  
  
 向右  
 要插入的物件或範圍。  
  
### <a name="remarks"></a>備註  
 建構函式：  
  
 `set();`  
  
 使用預設排序述詞，初始化受控制的序列的任何項目， `key_compare()`。 您可以使用它來指定空的初始受控制的序列，使用預設排序述詞。  
  
 建構函式：  
  
 `explicit set(key_compare^ pred);`  
  
 初始化受控制的序列沒有項目時，順序的述詞`pred`。 您可以使用它來指定空的初始受控制的序列，以指定順序的述詞。  
  
 建構函式：  
  
 `set(set<Key>% right);`  
  
 初始化受控制的序列與順序 [`right.begin()`， `right.end()`)，使用預設排序述詞。 您用它來指定是集合物件所控制之序列的複本初始受控制的序列`right`，排序述詞的預設值。  
  
 建構函式：  
  
 `set(set<Key>^ right);`  
  
 初始化受控制的序列與順序 [`right->begin()`， `right->end()`)，使用預設排序述詞。 您用它來指定是集合物件所控制之序列的複本初始受控制的序列`right`，排序述詞的預設值。  
  
 建構函式：  
  
 `template<typename InIter> set(InIter first, InIter last);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，使用預設排序述詞。 您可以使用它來製作受控制的序列的其他順序，排序述詞的預設值。  
  
 建構函式：  
  
 `template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，與順序的述詞`pred`。 您可以使用它來進行受控制的序列的指定順序的述詞的另一個序列的複本。  
  
 建構函式：  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，排序述詞的預設值。 您可以使用它來進行受控制的序列排序述詞的預設值所列舉值，描述的另一個序列的複本。  
  
 建構函式：  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，順序的述詞`pred`。 您可以使用它來進行受控制的序列的列舉值，指定順序的述詞所描述的另一個序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
// construct an empty container   
    Myset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 c b a  
 a b c  
 c b a  
 a b c  
 c b a  
 c b a  
 a b c  
```  

## <a name="size"></a> set:: size (STL/CLR)
計算元素的數目。  
  
### <a name="syntax"></a>語法  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的項目數。 如果您在意順序是否具有非零的大小，請參閱[set:: empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)`()`。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_size.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  

## <a name="size_type"></a> set:: size_type (STL/CLR)
兩個項目之間的帶正負號距離的類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述負的項目計數。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_size_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myset::size_type diff = 0;   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  

## <a name="swap"></a> set:: swap (STL/CLR)
交換兩個容器的內容。  
  
### <a name="syntax"></a>語法  
  
```  
void swap(set<Key>% right);  
```  
  
#### <a name="parameters"></a>參數  
 向右  
 要交換內容的容器。  
  
### <a name="remarks"></a>備註  
 成員函式會交換 `this` 和 `right` 之間受控制的序列。 它會以常數時間如此，就會擲回任何例外狀況。 您可以使用它做為交換兩個容器的內容的快速方式。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_swap.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myset c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
d e f  
d e f  
a b c  
```  
  
## <a name="to_array"></a> set::to_array (STL/CLR)
將受控制的序列複製到新的陣列。  
  
### <a name="syntax"></a>語法  
  
```  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回受控制的序列的陣列。 您可以使用它來取得陣列的形式受控制序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_to_array.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c d  
a b c  
```  

## <a name="upper_bound"></a> set:: upper_bound (STL/CLR)
尋找符合指定之索引鍵的範圍結尾。  
  
### <a name="syntax"></a>語法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 成員函式決定的最後一個項目`X`具有對等順序，來控制序列中`key`。 如果沒有這類元素存在，或如果`X`是最後一個項目，在受控制序列中，它會傳回[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; 否則它會傳回迭代器，指定之外的第一個項目`X`. 您可以使用它來目前受控制序列之符合指定之索引鍵中尋找的項目序列的結尾。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_upper_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = b  
*upper_bound(L'b') = c  
```  

## <a name="value_comp"></a> set:: value_comp (STL/CLR)
將複製兩個項目值的順序委派。  
  
### <a name="syntax"></a>語法  
  
```  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回用來排序受控制的序列的順序委派。 您可以使用它來比較兩個項目值。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_value_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_compare"></a> set:: value_compare (STL/CLR)
兩個項目值順序的委派。  
  
### <a name="syntax"></a>語法  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
### <a name="remarks"></a>備註  
 類型是委派，其值的引數的順序會決定的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_value_compare.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_type"></a> set:: value_type (STL/CLR)
元素的類型。  
  
### <a name="syntax"></a>語法  
  
```  
  
typedef generic_value value_type;  
  
```  
  
### <a name="remarks"></a>備註  
 這個類型與 `generic_value`同義。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_value_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myset::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="op_neq"></a> 運算子 ！ = (set) (STL/CLR)
列出不相等比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Key>  
    bool operator!=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(left == right)`。 使用它來測試是否`left`未經過排序相同`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_operator_ne.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  

## <a name="op_lt"></a> 運算子&lt;(set) (STL/CLR)
清單小於比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Key>  
    bool operator<(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式傳回 true，否則，最低的位置`i`其`!(right[i] < left[i])`是也是 true， `left[i] < right[i]`。 否則，它會傳回`left->size() < right->size()`使用它來測試是否`left`排序之前`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_operator_lt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> 運算子&lt;= (set) (STL/CLR)
小於或等於清單比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Key>  
    bool operator<=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(right < left)`。 使用它來測試是否`left`未經過排序之後`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_operator_le.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  
  
## <a name="op_eq"></a> 運算子 = = (set) (STL/CLR)
列出相等比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Key>  
    bool operator==(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回 true，只有當所控制的序列`left`和`right`具有相同長度和每個位置`i`， `left[i] ==` `right[i]`。 使用它來測試是否`left`排序相同`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_operator_eq.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  

## <a name="op_gt"></a> 運算子&gt;(set) (STL/CLR)
大於比較清單。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Key>  
    bool operator>(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`right` `<` `left`。 使用它來測試是否`left`排序後`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_operator_gt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  

## <a name="op_gteq"></a> 運算子&gt;= (set) (STL/CLR)
清單大於或等於比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Key>  
    bool operator>=(set<Key>% left,  
        set<Key>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(left < right)`。 使用它來測試是否`left`之前未經過排序`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_set_operator_ge.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  