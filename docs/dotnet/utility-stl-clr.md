---
title: 公用程式 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
dev_langs:
- C++
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fcc97e5037898b3a9c39a6c72ed21b2c19a4c777
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2018
ms.locfileid: "36306017"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)
包括 STL/CLR 標頭`<cliext/utility>`來定義範本類別`pair`和數個支援的樣板函式。  
  
## <a name="syntax"></a>語法  
  
```  
#include <utility>  
```

## <a name="requirements"></a>需求  
 **標頭：** \<cliext/公用程式 >  
  
 **命名空間：** cliext  
  
## <a name="declarations"></a>宣告  
  
|類別|描述|  
|-----------|-----------------|  
|[pair (STL/CLR)](#pair)|包裝元素配對。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[operator== (pair) (STL/CLR)](#op_eq)|配對相等比較。|  
|[operator!= (pair) (STL/CLR)](#op_neq)|配對不相等比較。|  
|[operator< (pair) (STL/CLR)](#op_lt)|配對小於比較。|  
|[運算子\<= （組） (STL/CLR)](#op_lteq)|小於或等於配對的比較。|  
|[operator> (pair) (STL/CLR)](#op_gt)|比較大於配對。|  
|[operator>= (pair) (STL/CLR)](#op_gteq)|對大於或等於比較。|  
  
|功能|描述|  
|--------------|-----------------|  
|[make_pair (STL/CLR)](#make_pair)|請從一組值的配對。|  

## <a name="members"></a>成員

##<a name="pair"></a> 配對 (STL/CLR)
此範本類別描述包裝一組值的物件。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### <a name="parameters"></a>參數  
 Value1  
 第一個包裝值類型。  
  
 Value2  
 第二個換行的值類型。  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[pair::first_type (STL/CLR)](#first_type)|第一個包裝的值類型。|  
|[pair::second_type (STL/CLR)](#second_type)|第二個包裝值類型。|  
  
|成員物件|描述|  
|-------------------|-----------------|  
|[pair::first (STL/CLR)](#first)|第一個預存的值。|  
|[pair::second (STL/CLR)](#second)|第二個儲存的值。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[pair::pair (STL/CLR)](#pair_pair)|建構組物件。|  
|[pair::swap (STL/CLR)](#swap)|交換兩對的內容。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[pair::operator= (STL/CLR)](#op_as)|取代預存的值的配對。|  
  
## <a name="remarks"></a>備註  
 此物件會儲存一組值。 您可以使用此範本類別，將兩個值結合成單一物件。 此外，物件`cliext::pair`（此處所述） 存放區僅限受管理類型; 若要儲存對 unmanaged 的類型使用`std::pair`中宣告`<utility>`。  


## <a name="first"></a> pair::first (STL/CLR)
第一個包裝的值。  
  
### <a name="syntax"></a>語法  
  
```  
Value1 first;  
```  
  
### <a name="remarks"></a>備註  
 此物件會儲存已包裝的第一個值。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_first.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  

## <a name="first_type"></a> pair::first_type (STL/CLR)
第一個包裝的值類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef Value1 first_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Value1`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_first_type.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  

## <a name="op_as"></a> pair::operator = (STL/CLR)
取代預存的值的配對。  
  
### <a name="syntax"></a>語法  
  
```  
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>參數  
 向右  
 要複製組。  
  
### <a name="remarks"></a>備註  
 成員運算子複製`right`物件，然後傳回`*this`。 您使用它來儲存一對值中的複本取代預存的值的配對`right`。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_operator_as.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
// assign to a new pair   
    cliext::pair<wchar_t, int> c2;   
    c2 = c1;   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 3]  
```  

## <a name="pair_pair"></a> pair::pair (STL/CLR)
建構組物件。  
  
### <a name="syntax"></a>語法  
  
```  
pair();  
pair(pair<Coll>% right);  
pair(pair<Coll>^ right);  
pair(Value1 val1, Value2 val2);  
```  
  
#### <a name="parameters"></a>參數  
 向右  
 要儲存組。  
  
 val1  
 要儲存的第一個值。  
  
 val2  
 要儲存的第二個值。  
  
### <a name="remarks"></a>備註  
 建構函式：  
  
 `pair();`  
  
 初始化具有預設建構值的預存的組。  
  
 建構函式：  
  
 `pair(pair<Value1, Value2>% right);`  
  
 初始化與預存的配對`right.` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)和`right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)。  
  
 `pair(pair<Value1, Value2>^ right);`  
  
 初始化與預存的配對`right->` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)和`right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)。  
  
 建構函式：  
  
 `pair(Value1 val1, Value2 val2);`  
  
 初始化具有與預存的組`val1`和`val2`。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_construct.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
// construct an empty container   
    cliext::pair<wchar_t, int> c1;   
    System::Console::WriteLine("[{0}, {1}]",   
        c1.first == L'\0' ? "\\0" : "??", c1.second);   
  
// construct with a pair of values   
    cliext::pair<wchar_t, int> c2(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
// construct by copying another pair   
    cliext::pair<wchar_t, int> c3(c2);   
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);   
  
// construct by copying a pair handle   
    cliext::pair<wchar_t, int> c4(%c3);   
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);   
  
    return (0);   
    }  
  
```  
  
```Output  
[\0, 0]  
[x, 3]  
[x, 3]  
[x, 3]  
```  

## <a name="second"></a> pair::second (STL/CLR)
第二個換行的值。  
  
### <a name="syntax"></a>語法  
  
```  
Value2 second;  
```  
  
### <a name="remarks"></a>備註  
 此物件會儲存已包裝的第二個值。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_second.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  

## <a name="second_type"></a> pair::second_type (STL/CLR)
第二個包裝值類型。  
  
### <a name="syntax"></a>語法  
  
```  
typedef Value2 second_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Value2`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_second_type.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```    

## <a name="swap"></a> pair::swap (STL/CLR)
交換兩對的內容。  
  
### <a name="syntax"></a>語法  
  
```  
void swap(pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>參數  
 向右  
 要交換內容的配對。  
  
### <a name="remarks"></a>備註  
 成員函式會交換預存的值之間的配對`*this`和`right`。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_swap.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::deque<wchar_t> d2(5, L'x');   
    Mycoll c2(%d2);   
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

## <a name="make_pair"></a> make_pair (STL/CLR)
請`pair`從一組值。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### <a name="parameters"></a>參數  
 `Value1`  
 第一個包裝的值類型。  
  
 `Value2`  
 第二個包裝值類型。  
  
 `first`  
 要包裝的第一個值。  
  
 `second`  
 第二個換行的值。  
  
### <a name="remarks"></a>備註  
 此範本函式會傳回 `pair<Value1, Value2>(first, second)`。 使用它來建構`pair<Value1, Value2>`從一組值的物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_make_pair.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    c1 = cliext::make_pair(L'y', 4);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[y, 4]  
```  

## <a name="op_neq"></a> 運算子 ！ = （組） (STL/CLR)
配對不相等比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator!=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左的組。  
  
 向右  
 要比較的右組。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(left == right)`。 使用它來測試是否`left`未經過排序相同`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp
// cliext_pair_operator_ne.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] != [x 3] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[x 3] != [x 4] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] != [x 3] is False  
[x 3] != [x 4] is True  
```  
  
## <a name="op_lt"></a> 運算子&lt;（組） (STL/CLR)
配對小於比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左的組。  
  
 向右  
 要比較的右組。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`。 使用它來測試是否`left`排序之前`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_operator_lt.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] < [x 3] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[x 3] < [x 4] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] < [x 3] is False  
[x 3] < [x 4] is True  
```  

## <a name="op_lteq"></a> 運算子&lt;= （組） (STL/CLR)
小於或等於配對的比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左的組。  
  
 向右  
 要比較的右組。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(right < left)`。 使用它來測試是否`left`未經過排序之後`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_operator_le.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] <= [x 3] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] <= [x 3] is True  
[x 4] <= [x 3] is False  
```  
  
## <a name="op_eq"></a> 運算子 = = （組） (STL/CLR)
配對相等比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator==(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左的組。  
  
 向右  
 要比較的右組。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`left.first ==` `right.first &&` `left.second ==` `right.second`。 使用它來測試是否`left`排序相同`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_operator_eq.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] == [x 3] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[x 3] == [x 4] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] == [x 3] is True  
[x 3] == [x 4] is False  
```  

## <a name="op_gt"></a> 運算子&gt;（組） (STL/CLR)
比較大於配對。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左的組。  
  
 向右  
 要比較的右組。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`right` `<` `left`。 使用它來測試是否`left`排序後`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_operator_gt.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] > [x 3] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[x 4] > [x 3] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] > [x 3] is False  
[x 4] > [x 3] is True  
```  

## <a name="op_gteq"></a> 運算子&gt;= （組） (STL/CLR)
對大於或等於比較。  
  
### <a name="syntax"></a>語法  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator>=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左的組。  
  
 向右  
 要比較的右組。  
  
### <a name="remarks"></a>備註  
 運算子函式會傳回`!(left < right)`。 使用它來測試是否`left`之前未經過排序`right`兩組時項目所比較的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// cliext_pair_operator_ge.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] >= [x 3] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] >= [x 3] is True  
[x 3] >= [x 4] is False  
```  
