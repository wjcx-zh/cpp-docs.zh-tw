---
title: 清單 (STL/CLR) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
dev_langs:
- C++
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8eb64c41db0e6062f2be636ddce7e8cefe0bb32b
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376286"
---
# <a name="list-stlclr"></a>list (STL/CLR)
此範本類別描述控制不同長度序列的項目可雙向存取的物件。 使用容器`list`來管理一系列的項目為雙向連結清單節點，各儲存一個項目。  
  
 下列描述中`GValue`等同*值*後者是 ref 型別，除非在此情況下是`Value^`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<typename Value>  
    ref class list  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        Microsoft::VisualC::StlClr::IList<GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>參數  
 *值*  
 受控制序列中項目的類型。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext 

## <a name="declarations"></a>宣告  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[list::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|  
|[list::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|  
|[list::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|  
|[list::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|  
|[list::generic_container (STL/CLR)](#generic_container)|容器的泛型介面型別。|  
|[list::generic_iterator (STL/CLR)](#generic_iterator)|泛型介面，該容器的迭代器類型。|  
|[list::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面的反向迭代器類型。|  
|[list::generic_value (STL/CLR)](#generic_value)|容器的泛型介面的項目型別。|  
|[list::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|  
|[list::reference (STL/CLR)](#reference)|項目的參考類型。|  
|[list::reverse_iterator (STL/CLR)](#reverse_iterator)|受控制序列的反向迭代器類型。|  
|[list::size_type (STL/CLR)](#size_type)|兩個項目之間帶正負號距離的類型。|  
|[list::value_type (STL/CLR)](#value_type)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[list::assign (STL/CLR)](#assign)|取代所有項目。|  
|[list::back (STL/CLR)](#back)|存取最後一個項目。|  
|[list::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|  
|[list::clear (STL/CLR)](#clear)|移除所有項目。|  
|[list::empty (STL/CLR)](#empty)|測試項目是否不存在。|  
|[list::end (STL/CLR)](#end)|指定受控制序列的結尾。|  
|[list::erase (STL/CLR)](#erase)|移除位於指定位置的項目。|  
|[list::front (STL/CLR)](#front)|存取第一個項目。|  
|[list::insert (STL/CLR)](#insert)|將項目加入指定的位置。|  
|[list::list (STL/CLR)](#list)|建構容器物件。|  
|[list::merge (STL/CLR)](#merge)|合併兩個已排序受控制的序列。|  
|[list::pop_back (STL/CLR)](#pop_back)|移除最後一個項目。|  
|[list::pop_front (STL/CLR)](#pop_front)|移除第一個項目。|  
|[list::push_back (STL/CLR)](#push_back)|加入新的最後一個項目。|  
|[list::push_front (STL/CLR)](#push_front)|加入新的第一個項目。|  
|[list::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|  
|[list::remove (STL/CLR)](#remove)|移除具有指定值的項目。|  
|[list::remove_if (STL/CLR)](#remove_if)|移除通過指定的測試的項目。|  
|[list::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|  
|[list::resize (STL/CLR)](#resize)|變更的項目數。|  
|[list::reverse (STL/CLR)](#reverse)|反轉受控制的序列。|  
|[list::size (STL/CLR)](#size)|計算元素的數目。|  
|[list::sort (STL/CLR)](#sort)|排序受控制的序列。|  
|[list::splice (STL/CLR)](#splice)|重新拼接節點之間的連結。|  
|[list::swap (STL/CLR)](#swap)|交換兩個容器的內容。|  
|[list::to_array (STL/CLR)](#to_array)|將受控制的序列複製到新的陣列。|  
|[list::unique (STL/CLR)](#unique)|移除通過指定測試的相鄰項目。|  
  
|屬性|描述|  
|--------------|-----------------|  
|[list::back_item (STL/CLR)](#back_item)|存取最後一個項目。|  
|[list::front_item (STL/CLR)](#front_item)|存取第一個項目。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[list::operator= (STL/CLR)](#op_as)|取代受控制的序列。|  
|[operator!= (list) (STL/CLR)](#op_neq)|決定是否`list`物件是否不等於另一個`list`物件。|  
|[operator< (list) (STL/CLR)](#op_lt)|決定是否`list`物件是否小於另一個`list`物件。|  
|[operator<= (list) (STL/CLR)](#op_lteq)|決定是否`list`物件是否小於或等於另一個`list`物件。|  
|[operator== (list) (STL/CLR)](#op_eq)|決定是否`list`物件是否等於另一個`list`物件。|  
|[operator> (list) (STL/CLR)](#op_gt)|決定是否`list`物件是否大於另一個`list`物件。|  
|[operator>= (list) (STL/CLR)](#op_gteq)|決定是否`list`物件是否大於或等於另一個`list`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|<xref:System.Collections.IEnumerable>|透過項目進行排序。|  
|<xref:System.Collections.ICollection>|維護項目群組。|  
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的項目進行排序。|  
|<xref:System.Collections.Generic.ICollection%601>|維護群組的具類型的項目。|  
|IList\<值 >|維護泛型容器。|  
  
## <a name="remarks"></a>備註  
 物件，配置並釋放它做為雙向連結清單中的個別節點所控制之序列的儲存體。 它會改變節點，不會將一個節點的內容複製到另一個之間的連結，重新排列項目。 這表示您可以插入和移除自由而不會干擾其餘元素的項目。 因此，清單是適合做為基礎的容器範本類別[佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)或樣板類別[堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)。  
  
 A`list`物件支援雙向迭代器，這表示您可以逐步執行至相鄰的項目指定的 iterator 可指定受控制序列中的項目。 特殊的前端節點會對應至所傳回的迭代器[list:: end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`。 如果有的話，您可以遞增到最後一個項目，在受控制序列中，此迭代器。 您可以遞增到前端節點時，清單迭代器，然後它會比較等於`end()`。 您無法取值 （dereference） 所傳回的迭代器，但`end()`。  
  
 請注意，您不能參考直接指定其數值位置-所需的隨機存取迭代器的清單項目。 因此清單*未*用作範本類別的基礎容器[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)。  
  
 清單中的迭代器會儲存其相關聯的清單 節點，接著會儲存其相關聯的容器的控制代碼的控制代碼。 您可以使用迭代器，只能搭配其相關聯的容器物件。 只要其相關聯的清單節點是與一些清單相關聯的清單迭代器會保持有效。 此外，有效的迭代器取值--您可以使用它來存取或修改的項目值，它會指定-只要不等於`end()`。  
  
 清除或移除一個項目呼叫解構函式，其預存值。 終結容器清除所有項目。 因此，的容器，其項目類型是 ref 類別可確保任何項目必須有存在的容器。 不過請注意，容器的控制代碼，並會*不*終結其項目。  
  
## <a name="members"></a>成員

## <a name="assign"></a> list:: assign (STL/CLR)
取代所有項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 *count*  
 要插入的元素數目。  
  
 *first*  
 若要插入的範圍的開頭。  
  
 *最後一個*  
 若要插入的範圍的結尾。  
  
 *right*  
 若要插入的列舉型別。  
  
 *val*  
 要插入之項目的值。  
  
### <a name="remarks"></a>備註  
 第一個成員函式會將受控制的序列取代重複*計數*值之項目的*val*。 您使用它來填滿容器項目全都具有相同的值。  
  
 如果`InIt`是整數類型，第二個成員函式的行為相同`assign((size_type)first, (value_type)last)`。 否則，它會取代受控制的序列序列 [`first`， `last`)。 您使用它來進行受控制的序列複本另一個序列。  
  
 第三個成員函式的列舉值所指定的序列取代受控制的序列*右*。 您可以使用它來進行受控制的序列的列舉值所描述的序列複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_assign.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    cliext::list<wchar_t>::iterator it = c1.end();   
    c2.assign(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  
 
## <a name="back"></a> list:: back (STL/CLR)
存取最後一個項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
reference back();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回受控制的序列必須為非空白的最後一個元素的參考。 您可以使用它來存取的最後一個元素，當您知道它存在。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
back() = c  
 a b x  
```  

## <a name="back_item"></a> list::back_item (STL/CLR)
存取最後一個項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
property value_type back_item;  
```  
  
### <a name="remarks"></a>備註  
 屬性存取受控制的序列必須為非空白的最後一個元素。 您可以使用它來讀取或寫入的最後一個元素，當您知道它存在。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_back_item.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  

## <a name="begin"></a> list:: begin (STL/CLR)
指定受控制序列的開頭。  
  
### <a name="syntax"></a>語法  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回指定之受控制的序列，或只是超出空序列結尾的第一個元素的隨機存取迭代器。 您用它來取得 iterator，指定`current`如果受控制序列的長度變更，可以變更受控制的序列，但其狀態的開頭。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_begin.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
 x y c  
```  

## <a name="clear"></a> list:: clear (STL/CLR)
移除所有項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void clear();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會有效地呼叫[list (STL/CLR):: erase](../dotnet/list-erase-stl-clr.md) `(` [list:: begin (STL/CLR)](../dotnet/list-begin-stl-clr.md) `(),` [list:: end (STL/CLR)](../dotnet/list-end-stl-clr.md) `())`. 您可以使用它來確保受控制的序列是空白。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_clear.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
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

## <a name="const_iterator"></a> list:: const_iterator (STL/CLR)
用於受控制序列的常數迭代器類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定型別的物件`T2`，可做為受控制序列的常數隨機存取迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_const_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> list:: const_reference (STL/CLR)
項目的常數參考類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述項目的常數參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_const_reference.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        cliext::list<wchar_t>::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> list:: const_reverse_iterator (STL/CLR)
受控制序列的常數反向迭代器的型別...  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定型別的物件`T4`，可做為受控制序列的常數反向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="difference_type"></a> list:: difference_type (STL/CLR)
兩個項目之間帶正負號距離的類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述的帶正負號的項目計數。  
  
### <a name="example"></a>範例  
  
```cpp 
// cliext_list_difference_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::list<wchar_t>::difference_type diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it) ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.end();   
        it != c1.begin(); --it) --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> list:: empty (STL/CLR)
測試項目是否不存在。  
  
### <a name="syntax"></a>語法  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會對空的受控制序列傳回 true。 它相當於[list:: size (STL/CLR)](../dotnet/list-size-stl-clr.md)`() == 0`。 您可以使用它來測試是否清單是空的。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_empty.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
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

## <a name="end"></a> list:: end (STL/CLR)
指定受控制序列的結尾。  
  
### <a name="syntax"></a>語法  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回指向受控制序列結尾之外的隨機存取迭代器。 您用它來取得 iterator，指定受控制序列中，結尾其狀態不變更如果受控制序列的長度變更。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_end.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::list<wchar_t>::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
 a x y  
```  

## <a name="erase"></a> list:: erase (STL/CLR)
移除位於指定位置的項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>參數  
 *first*  
 若要清除的範圍的開頭。  
  
 *最後一個*  
 若要清除的範圍的結尾。  
  
 *where*  
 若要清除的項目。  
  
### <a name="remarks"></a>備註  
 第一個成員函式會移除所指向之受控制序列的項目*其中*。 您可以使用它來移除單一項目。  
  
 第二個成員函式會移除 [`first`, `last`) 範圍中受控制序列中的元素。 您可以使用它來移除零或多個連續的項目。  
  
 這兩個成員函式會傳回迭代器，指定移除任何項目之外剩餘的第一個元素或[list:: end (STL/CLR)](../dotnet/list-end-stl-clr.md) `()`如果沒有這類項目。  
  
 當清除項目，項目複本數目中是線性清除端點與序列的最接近的結尾之間的項目數。 （當清除序列的任一端的一或多個項目，沒有項目複本會發生。）  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_erase.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::list<wchar_t>::iterator it = c1.end();   
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

## <a name="front"></a> list:: front (STL/CLR)
存取第一個項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
reference front();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回受控制的序列必須為非空白的第一個元素的參考。 您可以使用它來讀取或寫入第一個項目中，當您知道它存在。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
front() = a  
 x b c  
```  

## <a name="front_item"></a> list::front_item (STL/CLR)
存取第一個項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
property value_type front_item;  
```  
  
### <a name="remarks"></a>備註  
 屬性存取受控制的序列必須為非空白的第一個元素。 您可以使用它來讀取或寫入第一個項目中，當您知道它存在。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_front_item.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter first item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  

## <a name="generic_container"></a> list::generic_container (STL/CLR)
容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::  
    IList<generic_value>  
    generic_container;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述此範本的容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_generic_container.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(gc1->end(), L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push_back(L'e');   
  
    System::Collections::IEnumerator^ enum1 =   
        gc1->GetEnumerator();   
    while (enum1->MoveNext())   
        System::Console::Write(" {0}", enum1->Current);   
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

## <a name="generic_iterator"></a> list::generic_iterator (STL/CLR)
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
// cliext_list_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

## <a name="generic_reverse_iterator"></a> list::generic_reverse_iterator (STL/CLR)
反向迭代器，用於容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述的一般反向迭代器可以搭配此範本的容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a c c  
```  

## <a name="generic_value"></a> list::generic_value (STL/CLR)
使用容器的泛型介面的項目型別。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>備註  
 此類型所描述型別的物件`GValue`，描述與此範本的容器類別的泛型介面使用的預存的項目值。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_generic_value.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

## <a name="insert"></a> list:: insert (STL/CLR)
將項目加入指定的位置。  
  
### <a name="syntax"></a>語法  
  
```cpp  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 *count*  
 要插入的元素數目。  
  
 *first*  
 若要插入的範圍的開頭。  
  
 *最後一個*  
 若要插入的範圍的結尾。  
  
 *right*  
 若要插入的列舉型別。  
  
 *val*  
 要插入之項目的值。  
  
 *where*  
 在之前所要插入容器中的位置。  
  
### <a name="remarks"></a>備註  
 每個成員函式所指向的項目之前插入*其中*由剩餘運算元，在受控制序列中，指定的順序。  
  
 第一個成員函式插入值的項目*val* ，並傳回迭代器，指定新插入的項目。 您可以使用它來插入迭代器指定的位置之前的單一項目。  
  
 第二個成員函式會插入重複*計數*值之項目的*val*。 您可以使用它來插入零或多個連續項目也就是相同值的所有複本。  
  
 如果 `InIt` 是整數類型，第三個成員函式的行為即與 `insert(where, (size_type)first, (value_type)last)` 相同。 否則，它會插入序列 [`first`， `last`)。 您可以使用它來插入另一個序列中複製的零或多個連續的元素。  
  
 第四個成員函式會插入所指定的順序*右*。 您可以使用它來插入列舉值所描述的順序。  
  
 當插入的單一項目，項目複本數目中是線性序列的最接近的結尾插入點之間的項目數。 （當任一端的序列插入一或多個項目，沒有項目複本會發生。）如果`InIt`是輸入迭代器，第三個成員函式會有效地執行單一插入序列中每個項目。 否則，當插入`N`項目，項目複本數目中是線性`N`再加上的插入點之間最接近的序列結尾的項目數。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_insert.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using index   
    it = c2.begin();   
    ++it, ++it, ++it;   
    c2.insert(it, L'z');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  

## <a name="iterator"></a> list:: iterator (STL/CLR)
受控制序列之迭代器的類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定型別的物件`T1`，可做為受控制序列之隨機存取迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    it = c1.begin();   
    *it = L'x';   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
x b c  
```  

## <a name="list"></a> list:: list (STL/CLR)
建構容器物件。  
  
### <a name="syntax"></a>語法  
  
```cpp  
list();  
list(list<Value>% right);  
list(list<Value>^ right);  
explicit list(size_type count);  
list(size_type count, value_type val);  
template<typename InIt>  
    list(InIt first, InIt last);  
list(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 *count*  
 要插入的元素數目。  
  
 *first*  
 若要插入的範圍的開頭。  
  
 *最後一個*  
 若要插入的範圍的結尾。  
  
 *right*  
 要插入的物件或範圍。  
  
 *val*  
 要插入之項目的值。  
  
### <a name="remarks"></a>備註  
  
 建構函式：  
  
 `list();`  
  
 初始化含任何項目的受控制的序列。 您可以使用它來指定空的初始受控制的序列。  
  
 建構函式：  
  
 `list(list<Value>% right);`  
  
 初始化受控制的序列具有序列 [`right.begin()`， `right.end()`)。 您使用它來指定初始受控制的序列的清單物件所控制之序列的複本*右*。  
  
 建構函式：  
  
 `list(list<Value>^ right);`  
  
 初始化受控制的序列具有序列 [`right->begin()`， `right->end()`)。 您使用它來指定初始受控制的序列的清單物件控制代碼所控制之序列的複本*右*。  
  
 建構函式：  
  
 `explicit list(size_type count);`  
  
 初始化具有受控制的序列*計數*項目每個值`value_type()`。 您使用它來填滿容器項目所有需要的預設值。  
  
 建構函式：  
  
 `list(size_type count, value_type val);`  
  
 初始化具有受控制的序列*計數*項目每個值*val*。 您使用它來填滿容器項目全都具有相同的值。  
  
 建構函式：  
  
 `template<typename InIt>`  
  
 `list(InIt first, InIt last);`  
  
 初始化受控制的序列具有序列 [`first`， `last`)。 您可以使用它來進行受控制的序列的另一個序列的複本。  
  
 建構函式：  
  
 `list(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序*右*。 您可以使用它來進行受控制的序列的列舉值所描述的另一個序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_construct.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::list<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::list<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::list<wchar_t>::iterator it = c3.end();   
    cliext::list<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::list<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::list<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  

## <a name="merge"></a> list:: merge (STL/CLR)
合併兩個已排序受控制的序列。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void merge(list<Value>% right);  
template<typename Pred2>  
    void merge(list<Value>% right, Pred2 pred);  
```  
  
#### <a name="parameters"></a>參數  
 *預測*  
 項目組的比較子。  
  
 *right*  
 若要在合併的容器。  
  
### <a name="remarks"></a>備註  
 第一個成員函式會移除所控制的序列中的所有項目*右*並將其插入受控制序列中。 兩個序列必須依先前排序`operator<`-項目必須不能減少值中您的過程中透過其中一個序列。 產生的序列也按照`operator<`。 您可以使用此成員函式來合併成也會增加值的序列增加值的兩個序列。  
  
 第二個成員函式行為與第一個相同，不同之處在於序列都會按照`pred`  --  `pred(X, Y)`必須是 false 的任何項目`X`項目，後面`Y`序列中。 您可以使用它來合併兩個序列排序的述詞函式或您指定的委派。  
  
 同時函式會執行的穩定的合併--不是原始的受控制序列中的項目配對會反轉產生受控制序列中。 此外，如果某對元素`X`和`Y`產生的受控制序列中具有對等順序- `!(X < Y) && !(X < Y)` -從原始的受控制序列的項目出現在項目之前所控制的序列*正確*。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_merge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
typedef cliext::list<wchar_t> Mylist;   
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'c');   
    c1.push_back(L'e');   
  
// display initial contents " a c e"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    cliext::list<wchar_t> c2;   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
    c2.push_back(L'f');   
  
// display initial contents " b d f"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// merge and display   
    cliext::list<wchar_t> c3(c1);   
    c3.merge(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
  
// sort descending, merge descending, and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.merge(c1, cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 a c e  
 b d f  
 a b c d e f  
c2.size() = 0  
 e c a  
 f e d c b a  
 f e e d c c b a a  
c1.size() = 0  
```  

## <a name="op_as"></a> list::operator = (STL/CLR)
取代受控制的序列。  
  
### <a name="syntax"></a>語法  
  
```  
list<Value>% operator=(list<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *right*  
 要複製的容器。  
  
### <a name="remarks"></a>備註  
 成員運算子複製*右*物件，然後傳回`*this`。 您使用它來取代受控制的序列中的受控制序列的複本*右*。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_operator_as.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="pop_back"></a> list:: pop_back (STL/CLR)
移除最後一個項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void pop_back();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式中移除受控制的序列必須為非空白的最後一個元素。 您可以使用它來縮短後端的一個元素的清單。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_pop_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b  
```  

## <a name="pop_front"></a> list:: pop_front (STL/CLR)
移除第一個項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void pop_front();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式中移除受控制的序列必須為非空白的第一個元素。 您可以使用它來縮短清單前面的一個項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_pop_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_front();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
b c  
```  

## <a name="push_back"></a> list:: push_back (STL/CLR)
加入新的最後一個項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void push_back(value_type val);  
```  
  
### <a name="remarks"></a>備註  
 此成員函式插入值的項目`val`受控制序列的結尾。 您可以使用它來附加至清單的另一個項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_push_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  
  
## <a name="push_front"></a> list:: push_front (STL/CLR)
加入新的第一個項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void push_front(value_type val);  
```  
  
### <a name="remarks"></a>備註  
 此成員函式插入值的項目`val`受控制序列的開頭。 您可以使用它來在前面加上另一個項目清單。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_push_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_front(L'a');   
    c1.push_front(L'b');   
    c1.push_front(L'c');   
  
// display contents " c b a"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="rbegin"></a> list:: rbegin (STL/CLR)
指定反向受控制序列的開頭。  
  
### <a name="syntax"></a>語法  
  
```cpp  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回指定之受控制的序列，或只是超出空序列開頭的最後一個元素的反向迭代器。 因此，它會指定`beginning`反向序列。 您用它來取得 iterator，指定`current`如果受控制序列的長度變更，可以變更以反向順序顯示之受控制的序列，但其狀態的開頭。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_rbegin.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
 a y x  
```  

## <a name="reference"></a> list:: reference (STL/CLR)
項目的參考類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述項目的參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_reference.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::list<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::list<wchar_t>::reference ref = *it;   
  
        ref += (wchar_t)(L'A' - L'a');   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
A B C  
```  

## <a name="remove"></a> list:: remove (STL/CLR)
移除具有指定值的項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void remove(value_type val);  
```  
  
#### <a name="parameters"></a>參數  
 *val*  
 要移除之項目的值。  
  
### <a name="remarks"></a>備註  
 此成員函式，在受控制序列中移除項目`((System::Object^)val)->Equals((System::Object^)x)`為 true （如果有的話）。 您可以使用它來清除任意項目具有指定的值。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_remove.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove(L'A');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();  
  
// remove and redisplay   
    c1.remove(L'b');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a c  
```  

## <a name="remove_if"></a> list:: remove_if (STL/CLR)
移除通過指定的測試的項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Pred1>  
    void remove_if(Pred1 pred);  
```  
  
#### <a name="parameters"></a>參數  
 *預測*  
 若要移除的項目進行測試。  
  
### <a name="remarks"></a>備註  
 此成員函式會從受控制的序列 （清除） 中移除每個項目`X`為其`pred(X)`為 true。 您可以使用它來移除您指定為函式或委派都符合條件的所有項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_remove_if.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b b b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(   
        cliext::equal_to<wchar_t>(), L'd'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(   
        cliext::not_equal_to<wchar_t>(), L'b'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b b b c  
a b b b c  
b b b  
``` 

## <a name="rend"></a> list:: rend (STL/CLR)
指定反向受控制序列的結尾。  
  
### <a name="syntax"></a>語法  
  
```cpp  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式傳回的反向迭代器指向之外開頭之受控制序列。 因此，它會指定`end`反向序列。 您用它來取得 iterator，指定`current`如果受控制序列的長度變更，可以變更結尾以反向順序顯示之受控制的序列，但其狀態。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_rend.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
 y x c  
```  

## <a name="resize"></a> list:: resize (STL/CLR)
變更的項目數。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>參數  
 *new_size*  
 受控制序列的新大小。  
  
 *val*  
 填補項目的值。  
  
### <a name="remarks"></a>備註  
 成員函式同時確保[list:: size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()`通傳回*new_size*。 如果它必須進行受控制的序列更長，第一個成員函式值附加至元素`value_type()`，而第二個成員函式值附加至元素*val*。 若要讓受控制的序列更短，這兩個成員函式有效地清除最後一個項目[list:: size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size`時間。 您會使用它來確保受控制的序列有大小*new_size*、 修剪或填補目前受控制的序列。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_resize.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  

## <a name="reverse"></a> list:: reverse (STL/CLR)
反轉受控制的序列。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void reverse();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會反轉受控制序列中的所有項目的順序。 您可以使用它來反映項目清單。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_reverse.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// reverse and redisplay   
    c1.reverse();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
c b a  
```  

## <a name="reverse_iterator"></a> list:: reverse_iterator (STL/CLR)
受控制序列的反向迭代器類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
x b a  
```  
  
## <a name="size"></a> list:: size (STL/CLR)
計算元素的數目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列的項目數。 如果您在意順序是否有非零值的大小，請參閱[list (STL/CLR):: empty](../dotnet/list-empty-stl-clr.md)`()`。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_size.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
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

## <a name="size_type"></a> list:: size_type (STL/CLR)
兩個項目之間帶正負號距離的類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述的非負數的項目計數。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_size_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::list<wchar_t>::size_type diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```

## <a name="sort"></a> list:: sort (STL/CLR)
排序受控制的序列。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### <a name="parameters"></a>參數  
 *預測*  
 項目組的比較子。  
  
### <a name="remarks"></a>備註  
 第一個成員函式重新整理受控制序列中的項目，以便依排序`operator<`-項目不要降低值在您透過序列的過程。 您可以使用此成員函式來排序的順序，以遞增的順序。  
  
 第二個成員函式行為與第一個相同，不同之處在於，順序依`pred`  --  `pred(X, Y)`為 false 的任何項目`X`項目，後面`Y`結果序列中。 您可以使用它來排序的順序，您指定的述詞函式或委派中的順序。  
  
 同時函式會執行穩定的排序--在原始的受控制序列中的項目沒有任何一對已反轉結果的受控制序列中。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_sort.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
c b a  
a b c  
``` 

## <a name="splice"></a> list:: splice (STL/CLR)
Restitch 節點之間的連結。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>參數  
 *first*  
 若要連接之範圍的開頭。  
  
 *最後一個*  
 若要連接之範圍的結尾。  
  
 *right*  
 要從中分離的容器。  
  
 *where*  
 要連接之前的容器中的位置。  
  
### <a name="remarks"></a>備註  
 第一個成員函式會插入所控制的序列*右*指向的項目在受控制序列中由之前*其中*。 它也會移除所有項目從*右*。 (`%right`不得等於`this`。)您可以使用它要一份清單的所有連接至另一個。  
  
 第二個成員函式會移除所指向的項目*第一個*中所控制的序列*右*並將它插入受控制序列中的項目所指的之前*位置*. (如果`where` `==` `first` `||` `where` `== ++first`，不會變更。)您可以使用它來連接到另一個的一份清單的單一項目。  
  
 第三個成員函式會插入所指定的子範圍 [`first`， `last`) 所控制的序列從*右*指向受控制序列中的項目之前*其中*. 它也會做為原始子範圍移除所控制的序列*右*。 (如果`right` `==` `this`，範圍 [`first`， `last`) 不能包含所指向的項目*其中*。)您可以使用它來連接到另一個清單中的零或多個項目的序列。  
  
### <a name="example"></a>範例  
  
```cpp
// cliext_list_splice.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
c1.size() = 0  
 a b c  
 a  
 b c  
 b c a  
c2.size() = 0  
```    

## <a name="swap"></a> list:: swap (STL/CLR)
交換兩個容器的內容。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void swap(list<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *right*  
 要交換內容的容器。  
  
### <a name="remarks"></a>備註  
 此成員函式會交換之間受控制的序列`*this`並*右*。 它會以常數時間，就會擲回任何例外狀況。 您可以使用它作為兩個容器的內容交換的快速方法。  
  
### <a name="example"></a>範例  
  
```cpp 
// cliext_list_swap.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::list<wchar_t> c2(5, L'x');   
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
x x x x x  
x x x x x  
a b c  
```   

## <a name="to_array"></a> list::to_array (STL/CLR)
將受控制的序列複製到新的陣列。  
  
### <a name="syntax"></a>語法  
  
```cpp  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回包含之受控制的序列的陣列。 您可以使用它來取得陣列形式中受控制序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_to_array.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push_back(L'd');   
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

## <a name="unique"></a> list:: unique (STL/CLR)
移除通過指定測試的相鄰項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### <a name="parameters"></a>參數  
 *預測*  
 項目組的比較子。  
  
### <a name="remarks"></a>備註  
 移除 （清除） 之受控制序列的第一個成員函式會比較每個元素等於其前面的項目--如果項目`X`前面的項目`Y`並`X == Y`，成員函式會移除`Y`。 您使用它來移除所有保留一個複本的每個序列的相鄰項目，比較相等。 請注意，如果受控制的序列經過排序，例如透過呼叫[list (STL/CLR):: sort](../dotnet/list-sort-stl-clr.md)`()`，成員函式離開只有項目具有唯一值。 (也因此才名為終端方法)。  
  
 第二個成員函式行為與第一個相同，不同之處在於它會移除每個項目`Y`下列項目`X`讓`pred(X, Y)`。 您可以使用它來移除所有保留一個複本的每個序列的相鄰項目滿足述詞函式或您指定的委派。 請注意，如果受控制的序列經過排序，例如透過呼叫`sort(pred)`，成員函式會保留不需要與任何其他項目相等排序的元素。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a a b c  
a b c  
a a  
```  

## <a name="value_type"></a> list:: value_type (STL/CLR)
元素的類型。  
  
### <a name="syntax"></a>語法  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>備註  
 類型是範本參數的同義字*值*。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_value_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::list<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
``` 

## <a name="op_neq"></a> 運算子 ！ = （清單） (STL/CLR)
列出不相等比較。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Value>  
    bool operator!=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(left == right)`。 您會使用它來測試是否*左*未經過排序相同*右*當兩個清單都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_operator_ne.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
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

## <a name="op_lt"></a> 運算子&lt;（清單） (STL/CLR)
清單小於比較。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Value>  
    bool operator<(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式傳回則為 true，最低的位置`i`為其`!(right[i] < left[i])`也雖說， `left[i] < right[i]`。 否則，它會傳回`left->size() < right->size()`使用它來測試是否*左*排序之前*右*當兩個清單都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_operator_lt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
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

## <a name="op_lteq"></a> 運算子&lt;= （清單） (STL/CLR)
清單小於或等於比較。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Value>  
    bool operator<=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(right < left)`。 您會使用它來測試是否*左*未經過排序之後*右*當兩個清單都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_operator_le.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
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

## <a name="op_eq"></a> 運算子 = = （清單） (STL/CLR)
列出相等比較。  
  
### <a name="syntax"></a>語法  
  
```cpp 
template<typename Value>  
    bool operator==(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回 true 所控制的序列時，才*左*並*右*具有相同的長度和每個位置`i`， `left[i] ==` `right[i]`。 您會使用它來測試是否*左*排序相同*右*當兩個清單都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_operator_eq.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
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

## <a name="op_gt"></a> 運算子&gt;（清單） (STL/CLR)
大於比較的清單。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Value>  
    bool operator>(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`right` `<` `left`。 您會使用它來測試是否*左*經過排序之後*右*當兩個清單都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_operator_gt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
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

## <a name="op_gteq"></a> 運算子&gt;= （清單） (STL/CLR)
清單大於或等於比較。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Value>  
    bool operator>=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 *left*  
 要比較的左容器。  
  
 *right*  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(left` `<` `right)`。 您會使用它來測試是否*左*未經過排序再*右*當兩個清單都是由項目相比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_list_operator_ge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
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