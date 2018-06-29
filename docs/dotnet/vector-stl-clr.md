---
title: 向量 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
dev_langs:
- C++
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
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
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5d5b3e94b0b594174538aebe6542b04df7214f1b
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079808"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)
此範本類別描述控制不同長度序列的項目具有隨機存取的物件。 使用容器`vector`管理的項目序列，做為連續的區塊存放裝置。 區塊會實作為隨成長的陣列。  
  
 在以下描述`GValue`相同`Value`後者是 ref 型別，除非在這種情況下很`Value^`。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>參數  
 值  
 受控制序列中項目的類型。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  

## <a name="declarations"></a>宣告  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[vector::const_iterator (STL/CLR)](#const_iterator)|用於受控制序列的常數迭代器類型。|  
|[vector::const_reference (STL/CLR)](#const_reference)|項目的常數參考類型。|  
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|用於受控制序列的常數反向迭代器類型。|  
|[vector::difference_type (STL/CLR)](#difference_type)|兩個項目之間帶正負號距離的類型。|  
|[vector::generic_container (STL/CLR)](#generic_container)|容器的泛型介面型別。|  
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|泛型介面，該容器的迭代器類型。|  
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型介面的反向迭代器類型。|  
|[vector::generic_value (STL/CLR)](#generic_value)|泛型介面的容器項目的類型。|  
|[vector::iterator (STL/CLR)](#iterator)|受控制序列之迭代器的類型。|  
|[vector::reference (STL/CLR)](#reference)|項目的參考類型。|  
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|受控制序列的反向迭代器類型。|  
|[vector::size_type (STL/CLR)](#size_type)|兩個項目之間帶正負號距離的類型。|  
|[vector::value_type (STL/CLR)](#value_type)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[vector::assign (STL/CLR)](#assign)|取代所有項目。|  
|[vector::at (STL/CLR)](#at)|存取指定位置的項目。|  
|[vector::back (STL/CLR)](#back)|存取最後一個項目。|  
|[vector::begin (STL/CLR)](#begin)|指定受控制序列的開頭。|  
|[vector::capacity (STL/CLR)](#capacity)|報表配置的儲存體容器的大小。|  
|[vector::clear (STL/CLR)](#clear)|移除所有項目。|  
|[vector::empty (STL/CLR)](#empty)|測試項目是否不存在。|  
|[vector::end (STL/CLR)](#end)|指定受控制序列的結尾。|  
|[vector::erase (STL/CLR)](#erase)|移除位於指定位置的項目。|  
|[vector::front (STL/CLR)](#front)|存取第一個項目。|  
|[vector::insert (STL/CLR)](#insert)|將項目加入指定的位置。|  
|[vector::pop_back (STL/CLR)](#pop_back)|移除最後一個項目。|  
|[vector::push_back (STL/CLR)](#push_back)|加入新的最後一個項目。|  
|[vector::rbegin (STL/CLR)](#rbegin)|指定反向受控制序列的開頭。|  
|[vector::rend (STL/CLR)](#rend)|指定反向受控制序列的結尾。|  
|[vector::reserve (STL/CLR)](#reserve)|可確保容器的最小的成長容量。|  
|[vector::resize (STL/CLR)](#resize)|變更項目數目。|  
|[vector::size (STL/CLR)](#size)|計算元素的數目。|  
|[vector::swap (STL/CLR)](#swap)|交換兩個容器的內容。|  
|[vector::to_array (STL/CLR)](#to_array)|將受控制的序列複製到新的陣列。|  
|[vector::vector (STL/CLR)](#vector)|建構容器物件。|  
  
|屬性|描述|  
|--------------|-----------------|  
|[vector::back_item (STL/CLR)](#back_item)|存取最後一個項目。|  
|[vector::front_item (STL/CLR)](#front_item)|存取第一個項目。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[vector::operator= (STL/CLR)](#op_as)|取代受控制的序列。|  
|[vector::operator (STL/CLR)](#op)|存取指定位置的項目。|  
|[operator!= (vector) (STL/CLR)](#op_neq)|決定如果`vector`物件是否不等於另一個`vector`物件。|  
|[operator< (vector) (STL/CLR)](#op_lt)|決定如果`vector`物件是否小於另一個`vector`物件。|  
|[operator<= (vector) (STL/CLR)](#op_lteq)|決定如果`vector`物件是否小於或等於另一個`vector`物件。|  
|[operator== (vector) (STL/CLR)](#op_eq)|決定如果`vector`物件是否等於另一個`vector`物件。|  
|[operator> (vector) (STL/CLR)](#op_gt)|決定如果`vector`物件是否大於另一個`vector`物件。|  
|[operator>= (vector) (STL/CLR)](#op_gteq)|決定如果`vector`物件是否大於或等於另一個`vector`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|<xref:System.Collections.IEnumerable>|項目順序。|  
|<xref:System.Collections.ICollection>|維護群組的項目。|  
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的項目順序。|  
|<xref:System.Collections.Generic.ICollection%601>|維護群組的具類型的項目。|  
|<xref:System.Collections.Generic.IList%601>|維護已排序的群組的具類型的項目。|  
|IVector < 值\>|維護泛型容器。|  
  
## <a name="remarks"></a>備註  
 物件可配置及釋放的序列的預存陣列透過它所控制的儲存體`Value`項目，則視成長。 附加新元素的成本是平攤常數時間的方式，就會發生成長。 換句話說，將項目結尾的成本不會增加，平均而言為受控制的序列愈大的長度。 因此，向量為基礎容器樣板類別的候選[堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)。  
  
 A`vector`支援隨機存取迭代器，這表示您可以參考項目直接指定其數值位置，從第一個 （前端） 項目的零計數來`size() - 1`的最後一個 （回到） 項目。 這也表示向量為基礎容器樣板類別的候選[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)。  
  
 向量的迭代器會儲存其相關聯的向量物件，以及它所指定的項目偏差的控制代碼。 您可以使用迭代器，只能使用其相關聯的容器物件。 向量項目偏差等同於其位置。  
  
 插入或刪除項目可以變更項目值的指定位置，儲存，因此也可以變更由迭代器指定的值。 （若要複製項目向上或向下建立一個洞之前插入或用來填入暴露在清除之後可能有容器）。不過，向量迭代器就持續有效，只要其偏差是在範圍中`[0, size()]`。 此外，有效的迭代器會維持 dereferencable-您可用它來存取或修改項目值，它會指定-，只要其偏差值不等於`size()`。  
  
 清除，或移除項目會呼叫解構函式的儲存值。 終結容器清除所有項目。 因此，其項目類型是 ref 類別的容器可確保，任何項目存留期比長容器。 不過請注意，容器的控制代碼不會終結其項目。  
  
## <a name="members"></a>成員

## <a name="assign"></a> vector:: assign (STL/CLR)
取代所有項目。  
  
### <a name="syntax"></a>語法  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 count  
 要插入的元素數目。  
  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 向右  
 若要插入的列舉型別。  
  
 Val  
 要插入之項目的值。  
  
### <a name="remarks"></a>備註  
 第一個成員函式取代重複的受控制的序列`count`值的項目`val`。 您使用它來填入項目容器全都具有相同的值。  
  
 如果`InIt`是整數類型，第二個成員函式的行為相同`assign((size_type)first, (value_type)last)`。 否則，它會取代受控制的序列的順序 [`first`， `last`)。 您使用它來進行受控制的序列複製另一個序列。  
  
 第三個成員函式的列舉值所指定的順序，取代受控制的序列`right`。 您可以使用它來製作受控制的序列的序列所描述的列舉值。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_assign.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
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

## <a name="at"></a> vector:: at (STL/CLR)
存取指定位置的項目。  
  
### <a name="syntax"></a>語法  
  
```  
reference at(size_type pos);  
```  
  
#### <a name="parameters"></a>參數  
 pos  
 要存取的項目的位置。  
  
### <a name="remarks"></a>備註  
 成員函式傳回的參考位置的受控制序列的項目`pos`。 您使用它來讀取或寫入項目，其位置您知道。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_at.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using at   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1.at(1) = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  

## <a name="back"></a> vector:: back (STL/CLR)
存取最後一個項目。  
  
### <a name="syntax"></a>語法  
  
```  
reference back();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回受控制的序列必須為非空白的最後一個元素的參考。 您可以使用它來存取最後一個項目中，當您知道它存在。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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

## <a name="back_item"></a> vector::back_item (STL/CLR)
存取最後一個項目。  
  
### <a name="syntax"></a>語法  
  
```  
property value_type back_item;  
```  
  
### <a name="remarks"></a>備註  
 屬性存取受控制的序列必須為非空白的最後一個元素。 您可以使用它來讀取或寫入的最後一個項目，當您知道它存在。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_back_item.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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

## <a name="begin"></a> vector:: begin (STL/CLR)
指定受控制序列的開頭。  
  
### <a name="syntax"></a>語法  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回指定的受控制序列中，或空序列結尾之外的第一個元素的隨機存取迭代器。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更受控制的序列中，但其狀態的開頭。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_begin.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
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

## <a name="capacity"></a> vector:: capacity (STL/CLR)
報表配置的儲存體容器的大小。  
  
### <a name="syntax"></a>語法  
  
```  
size_type capacity();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回目前配置給保留受控制的序列的值至少一樣大的儲存體[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`。 您可以使用它來判斷多少容器之前它就必須重新配置受控制序列的儲存體所能成長。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_capacity.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  

## <a name="clear"></a> vector:: clear (STL/CLR)
移除所有項目。  
  
### <a name="syntax"></a>語法  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>備註  
 成員函式可有效地呼叫[vector:: erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(` [vector:: begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md) `(),` [vector:: end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `())`. 您可以使用它來確定受控制的序列是空白。  
  
### <a name="example"></a>範例  
  
```  
// cliext_vector_clear.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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

## <a name="const_iterator"></a> vector:: const_iterator (STL/CLR)
用於受控制序列的常數迭代器類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T2`，可做為受控制序列的常數隨機存取迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_const_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> vector:: const_reference (STL/CLR)
項目的常數參考類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述項目的常數參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_const_reference.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        cliext::vector<wchar_t>::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> vector:: const_reverse_iterator (STL/CLR)
受控制序列的常數反向迭代器型別...  
  
### <a name="syntax"></a>語法  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T4`，可做為受控制序列的常數反向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="difference_type"></a> vector:: difference_type (STL/CLR)
兩個項目之間的帶正負號距離的類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述的帶正負號的項目計數。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_difference_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::vector<wchar_t>::difference_type diff = 0;   
    for (cliext::vector<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it) ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (cliext::vector<wchar_t>::iterator it = c1.end();   
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

## <a name="empty"></a> vector:: empty (STL/CLR)
測試項目是否不存在。  
  
### <a name="syntax"></a>語法  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會對空的受控制序列傳回 true。 它相當於[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() == 0`。 您可以使用它來測試是否向量是空的。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_empty.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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

## <a name="end"></a> vector:: end (STL/CLR)
指定受控制序列的結尾。  
  
### <a name="syntax"></a>語法  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回指向受控制序列的結尾之外的隨機存取迭代器。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更結尾受控制的序列中，但它的狀態。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_end.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::vector<wchar_t>::iterator it = c1.end();   
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

## <a name="erase"></a> vector:: erase (STL/CLR)
移除位於指定位置的項目。  
  
### <a name="syntax"></a>語法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 要清除範圍的開頭。  
  
 last  
 若要清除的範圍的結尾。  
  
 其中  
 若要清除的項目。  
  
### <a name="remarks"></a>備註  
 第一個成員函式會移除 `where` 所指向之受控制序列中的項目。 您可以使用它來移除單一項目。  
  
 第二個成員函式會移除 [`first`, `last`) 範圍中受控制序列中的元素。 您可以使用它來移除零或多個連續的項目。  
  
 這兩個成員函式會傳回指定任何移除的項目之外剩餘的第一個元素的迭代器或[vector:: end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `()`如果沒有這類元素存在。  
  
 當清除項目，項目複本數目中是線性清除結尾之間距離越近序列結尾的項目數。 （當清除序列的任一端的一或多個項目，沒有項目複本會發生。）  
  
### <a name="example"></a>範例  
  
```cpp 
// cliext_vector_erase.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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
    cliext::vector<wchar_t>::iterator it = c1.end();   
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

## <a name="front"></a> vector:: front (STL/CLR)
存取第一個項目。  
  
### <a name="syntax"></a>語法  
  
```  
reference front();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回受控制的序列必須為非空白的第一個元素的參考。 您可以使用它來讀取或寫入第一個項目中，當您知道它存在。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_front.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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

# <a name="front_item"></a> vector::front_item (STL/CLR)
存取第一個項目。  
  
### <a name="syntax"></a>語法  
  
```  
property value_type front_item;  
```  
  
### <a name="remarks"></a>備註  
 屬性存取受控制的序列必須為非空白的第一個項目。 您可以使用它來讀取或寫入第一個項目中，當您知道它存在。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_front_item.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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

# <a name="generic_container"></a> vector::generic_container (STL/CLR)
容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```  
typedef Microsoft::VisualC::StlClr::  
    IVector<generic_value>  
    generic_container;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述此樣板容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_generic_container.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
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

## <a name="generic_iterator"></a> vector::generic_iterator (STL/CLR)
迭代器使用容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerRandomAccessIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型所描述泛型的迭代器，可以搭配這個範本容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
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

# <a name="generic_reverse_iterator"></a> vector::generic_reverse_iterator (STL/CLR)
反向迭代器使用容器的泛型介面型別。  
  
### <a name="syntax"></a>語法  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型所描述泛型反向迭代器，可以搭配這個範本容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
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

## <a name="generic_value"></a> vector::generic_value (STL/CLR)
使用容器的泛型介面的項目類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>備註  
 此類型所描述型別的物件`GValue`描述使用的預存的項目值與此範本容器類別的泛型介面。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_generic_value.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
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

## <a name="insert"></a> vector:: insert (STL/CLR)
將項目加入指定的位置。  
  
### <a name="syntax"></a>語法  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 count  
 要插入的元素數目。  
  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 向右  
 若要插入的列舉型別。  
  
 Val  
 要插入之項目的值。  
  
 其中  
 在前面插入的容器中的位置。  
  
### <a name="remarks"></a>備註  
 每個成員函式所指向的項目之前插入`where`其餘運算元所指定受控制序列中中, 序列。  
  
 第一個成員函式插入值的項目`val`並傳回指定的新插入的元素的迭代器。 您可以使用它來插入迭代器指定的位置之前的單一項目。  
  
 第二個成員函式會插入 `val` 值的 `count` 個元素數重複。 您可以使用它來插入零或多個連續的項目也就是相同值的所有複本。  
  
 如果 `InIt` 是整數類型，第三個成員函式的行為即與 `insert(where, (size_type)first, (value_type)last)` 相同。 否則，它會插入序列 [`first`， `last`)。 您可以使用它來插入另一個序列中複製的零或多個連續的元素。  
  
 第四個成員函式會插入所指定的序列`right`。 您可以使用它來插入列舉所描述的順序。  
  
 當插入單一項目，項目複本數目中是線性的插入點之間距離越近序列結尾的項目數。 （當插入順序的任一端的一或多個項目，沒有項目複本會發生。）如果`InIt`是輸入的迭代器，第三個成員函式會有效地執行單一插入每個項目序列中。 否則，當插入`N`項目，項目複本數目中是線性`N`加上數字的項目插入點之間距離越近序列的結尾。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_insert.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::vector<wchar_t> c2;   
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
  
## <a name="iterator"></a> vector:: iterator (STL/CLR)
受控制序列之迭代器的類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T1`，可做為受控制序列之隨機存取迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
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

## <a name="op_as"></a> vector:: operator = (STL/CLR)
取代受控制的序列。  
  
### <a name="syntax"></a>語法  
  
```  
vector<Value>% operator=(vector<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 向右  
 要複製的容器。  
  
### <a name="remarks"></a>備註  
 成員運算子複製`right`物件，然後傳回`*this`。 您使用它將受控制序列取代為 `right` 中受控制序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_operator_as.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
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

## <a name="op"></a> vector::operator(STL/CLR)
存取指定位置的項目。  
  
### <a name="syntax"></a>語法  
  
```  
reference operator[](size_type pos);  
```  
  
#### <a name="parameters"></a>參數  
 pos  
 要存取的項目的位置。  
  
### <a name="remarks"></a>備註  
 成員運算子會傳回 referene 位置的項目至`pos`。 您可以使用它來存取您知道其位置的項目。  
  
### <a name="example"></a>範例  
  
```cpp 
// cliext_vector_operator_sub.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using subscripting   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1[1] = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  

## <a name="pop_back"></a> vector:: pop_back (STL/CLR)
移除最後一個項目。  
  
### <a name="syntax"></a>語法  
  
```  
void pop_back();  
```  
  
### <a name="remarks"></a>備註  
 成員函式中移除受控制的序列必須為非空白的最後一個元素。 您可以使用它來縮短向量在最後一個項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_pop_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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

## <a name="push_back"></a> vector:: push_back (STL/CLR)
加入新的最後一個項目。  
  
### <a name="syntax"></a>語法  
  
```  
void push_back(value_type val);  
```  
  
### <a name="remarks"></a>備註  
 成員函式插入值的項目`val`受控制序列的結尾。 您可以使用它來將另一個項目附加至向量。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_push_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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
  
## <a name="rbegin"></a> vector:: rbegin (STL/CLR)
指定反向受控制序列的開頭。  
  
### <a name="syntax"></a>語法  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回指定受控制序列中，或空的序列開頭以外路徑的最後一個元素的反向迭代器。 因此，它會指定`beginning`反向序列。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更受控制的序列相反的順序出現，但其狀態的開頭。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_rbegin.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
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

## <a name="reference"></a> vector:: reference (STL/CLR)
項目的參考類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述項目的參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_reference.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::vector<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::vector<wchar_t>::reference ref = *it;   
  
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

## <a name="rend"></a> vector:: rend (STL/CLR)
指定反向受控制序列的結尾。  
  
### <a name="syntax"></a>語法  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回以外的位置開始，指向受控制序列的反向迭代器。 因此，它會指定`end`反向序列。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更結尾受控制的序列相反的順序出現，但它的狀態。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_rend.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();   
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

## <a name="reserve"></a> vector:: reserve (STL/CLR)
可確保容器的最小的成長容量。  
  
### <a name="syntax"></a>語法  
  
```  
void reserve(size_type count);  
```  
  
#### <a name="parameters"></a>參數  
 count  
 新容器的最大容量。  
  
### <a name="remarks"></a>備註  
 成員函式可確保`capacity()`從此以後傳回至少`count`。 您可以使用它來確保，容器需要重新配置受控制序列的儲存體之前，它就成長為指定的大小。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_reserve.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  

## <a name="resize"></a> vector:: resize (STL/CLR)
變更項目數目。  
  
### <a name="syntax"></a>語法  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>參數  
 new_size  
 新的受控制序列的大小。  
  
 Val  
 填補項目的值。  
  
### <a name="remarks"></a>備註  
 成員函式同時確保[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()`從此以後傳回`new_size`。 如果第一個成員函式必須讓受控制的序列更長，即會將 `value_type()` 值附加至元素，而第二個成員函式會將 `val` 值附加至元素。 若要使較短的受控制的序列，這兩個成員函式有效地清除最後一個項目[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size`時間。 您使用它來確保受控制的序列的大小`new_size`、 修剪或填補目前受控制的序列。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
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

## <a name="reverse_iterator"></a> vector:: reverse_iterator (STL/CLR)
受控制序列的反向迭代器類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
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

## <a name="size"></a> vector:: size (STL/CLR)
計算元素的數目。  
  
### <a name="syntax"></a>語法  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的項目數。 如果您在意順序是否具有非零的大小，請參閱[vector:: empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)`()`。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_size.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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

## <a name="size_type"></a> vector:: size_type (STL/CLR)
兩個項目之間帶正負號距離的類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述負的項目計數。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_size_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  
  
## <a name="swap"></a> vector:: swap (STL/CLR)
交換兩個容器的內容。  
  
### <a name="syntax"></a>語法  
  
```  
void swap(vector<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 向右  
 要交換內容的容器。  
  
### <a name="remarks"></a>備註  
 成員函式會交換 `*this` 和 `right` 之間受控制的序列。 它會以常數時間如此，就會擲回任何例外狀況。 您可以使用它做為交換兩個容器的內容的快速方式。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_swap.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::vector<wchar_t> c2(5, L'x');   
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

## <a name="to_array"></a> vector::to_array (STL/CLR)
將受控制的序列複製到新的陣列。  
  
### <a name="syntax"></a>語法  
  
```  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回受控制的序列的陣列。 您可以使用它來取得陣列的形式受控制序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_to_array.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
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

## <a name="value_type"></a> vector:: value_type (STL/CLR)
元素的類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Value`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_value_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::vector<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::vector<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="vector"></a> vector:: vector (STL/CLR)
建構容器物件。  
  
### <a name="syntax"></a>語法  
  
```  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 count  
 要插入的元素數目。  
  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 向右  
 要插入的物件或範圍。  
  
 Val  
 要插入之項目的值。  
  
### <a name="remarks"></a>備註  
 建構函式：  
  
 `vector();`  
  
 初始化受控制的序列為沒有項目。 您可以用它來指定空的初始受控制的序列。  
  
 建構函式：  
  
 `vector(vector<Value>% right);`  
  
 初始化受控制的序列與順序 [`right.begin()`， `right.end()`)。 您用它來指定的向量物件所控制之序列的複本初始受控制的序列`right`。  
  
 建構函式：  
  
 `vector(vector<Value>^ right);`  
  
 初始化受控制的序列與順序 [`right->begin()`， `right->end()`)。 您用它來指定其控制代碼的向量物件所控制之序列的複本初始受控制的序列`right`。  
  
 建構函式：  
  
 `explicit vector(size_type count);`  
  
 初始化具有受控制的序列`count`項目每個值`value_type()`。 您使用它來填入項目容器全都具有預設值。  
  
 建構函式：  
  
 `vector(size_type count, value_type val);`  
  
 初始化具有受控制的序列`count`項目每個值`val`。 您使用它來填入項目容器全都具有相同的值。  
  
 建構函式：  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 初始化受控制的序列與順序 [`first`， `last`)。 您可以使用它來進行受控制的序列的另一個序列的複本。  
  
 建構函式：  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`。 您可以使用它來進行受控制的序列的列舉值所描述的另一個序列的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
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

## <a name="op_neq"></a> 運算子 ！ = （向量） (STL/CLR)
向量不等於比較。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<typename Value>  
    bool operator!=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(left == right)`。 使用它來測試是否`left`未經過排序相同`right`兩個向量時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_operator_ne.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
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

## <a name="op_lt"></a> 運算子&lt;（向量） (STL/CLR)
向量小於比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    bool operator<(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式傳回 true，否則，最低的位置`i`其`!(right[i] < left[i])`是也是 true， `left[i] < right[i]`。 否則，它會傳回`left->size() < right->size()`使用它來測試是否`left`排序之前`right`兩個向量時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_operator_lt.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
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

## <a name="op_lteq"></a> 運算子&lt;= （向量） (STL/CLR)
向量小於或等於比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    bool operator<=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(right < left)`。 使用它來測試是否`left`未經過排序之後`right`兩個向量時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_operator_le.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
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

## <a name="op_eq"></a> 運算子 = = （向量） (STL/CLR)
向量相等比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    bool operator==(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回 true，只有當所控制的序列`left`和`right`具有相同長度和每個位置`i`， `left[i] ==` `right[i]`。 使用它來測試是否`left`排序相同`right`兩個向量時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_operator_eq.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
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

## <a name="op_gt"></a> 運算子&gt;（向量） (STL/CLR)
大於比較的向量。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    bool operator>(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`right` `<` `left`。 使用它來測試是否`left`排序後`right`兩個向量時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_operator_gt.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
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

## <a name="op_gteq"></a> 運算子&gt;= （向量） (STL/CLR)
向量大於或等於比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    bool operator>=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(left < right)`。 使用它來測試是否`left`之前未經過排序`right`兩個向量時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_vector_operator_ge.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
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
