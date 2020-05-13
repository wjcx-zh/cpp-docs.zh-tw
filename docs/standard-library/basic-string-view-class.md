---
title: basic_string_view 類別
ms.date: 04/20/2019
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::iterator
- xstring/std::basic_string_view::npos
- xstring/std::basic_string_view::pointer
- xstring/std::basic_string_view::reference
- xstring/std::basic_string_view::reverse_iterator
- xstring/std::basic_string_view::size_type
- xstring/std::basic_string_view::traits_type
- xstring/std::basic_string_view::value_type
- xstring/std::basic_string_view::append
- xstring/std::basic_string_view::assign
- xstring/std::basic_string_view::at
- xstring/std::basic_string_view::back
- xstring/std::basic_string_view::begin
- xstring/std::basic_string_view::c_str
- xstring/std::basic_string_view::capacity
- xstring/std::basic_string_view::cbegin
- xstring/std::basic_string_view::cend
- xstring/std::basic_string_view::clear
- xstring/std::basic_string_view::compare
- xstring/std::basic_string_view::copy
- xstring/std::basic_string_view::_Copy_s
- xstring/std::basic_string_view::crbegin
- xstring/std::basic_string_view::crend
- xstring/std::basic_string_view::data
- xstring/std::basic_string_view::empty
- xstring/std::basic_string_view::end
- xstring/std::basic_string_view::erase
- xstring/std::basic_string_view::find
- xstring/std::basic_string_view::find_first_not_of
- xstring/std::basic_string_view::find_first_of
- xstring/std::basic_string_view::find_last_not_of
- xstring/std::basic_string_view::find_last_of
- xstring/std::basic_string_view::front
- xstring/std::basic_string_view::get_allocator
- xstring/std::basic_string_view::insert
- xstring/std::basic_string_view::length
- xstring/std::basic_string_view::max_size
- xstring/std::basic_string_view::pop_back
- xstring/std::basic_string_view::push_back
- xstring/std::basic_string_view::rbegin
- xstring/std::basic_string_view::rend
- xstring/std::basic_string_view::remove_prefix
- xstring/std::basic_string_view::remove_suffix
- xstring/std::basic_string_view::replace
- xstring/std::basic_string_view::reserve
- xstring/std::basic_string_view::resize
- xstring/std::basic_string_view::rfind
- xstring/std::basic_string_view::shrink_to_fit
- xstring/std::basic_string_view::size
- xstring/std::basic_string_view::substr
- xstring/std::basic_string_view::swap
helpviewer_keywords:
- std::basic_string_view
- std::basic_string_view, allocator_type
- std::basic_string_view, const_iterator
- std::basic_string_view, const_pointer
- std::basic_string_view, const_reference
- std::basic_string_view, const_reverse_iterator
- std::basic_string_view, difference_type
- std::basic_string_view, iterator
- std::basic_string_view, npos
- std::basic_string_view, pointer
- std::basic_string_view, reference
- std::basic_string_view, reverse_iterator
- std::basic_string_view, size_type
- std::basic_string_view, traits_type
- std::basic_string_view, value_type
- std::basic_string_view, append
- std::basic_string_view, assign
- std::basic_string_view, at
- std::basic_string_view, back
- std::basic_string_view, begin
- std::basic_string_view, c_str
- std::basic_string_view, capacity
- std::basic_string_view, cbegin
- std::basic_string_view, cend
- std::basic_string_view, clear
- std::basic_string_view, compare
- std::basic_string_view, copy
- std::basic_string_view, crbegin
- std::basic_string_view, crend
- std::basic_string_view, data
- std::basic_string_view, empty
- std::basic_string_view, end
- std::basic_string_view, erase
- std::basic_string_view, find
- std::basic_string_view, find_first_not_of
- std::basic_string_view, find_first_of
- std::basic_string_view, find_last_not_of
- std::basic_string_view, find_last_of
- std::basic_string_view, front
- std::basic_string_view, get_allocator
- std::basic_string_view, insert
- std::basic_string_view, length
- std::basic_string_view, max_size
- std::basic_string_view, pop_back
- std::basic_string_view, push_back
- std::basic_string_view, rbegin
- std::basic_string_view, rend
- std::basic_string_view, remove_prefix
- std::basic_string_view, remove_suffix
- std::basic_string_view, replace
- std::basic_string_view, reserve
- std::basic_string_view, resize
- std::basic_string_view, rfind
- std::basic_string_view, shrink_to_fit
- std::basic_string_view, size
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: ac65dca931f821c717e9c081c8d3479fd0b3bb0e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364898"
---
# <a name="basic_string_view-class"></a>basic_string_view 類別

類範本`basic_string_view<charT>`在 C++17 中添加,作為函數接受各種不相關的字串類型的一種安全有效的方法,而無需對這些類型進行範本化。 類包含指向連續字元數據序列的非擁有指標,以及指定序列中字元數的長度。 對於序列是否為 null 終止,不進行假設。

標準函式庫根據元素的型態定義多個專門化:

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

在本文檔中,"string_view"一詞通常是指其中任何一個類型。

string_view描述讀取字串資料所需的最小公共介面。 它提供了對基礎數據的一致訪問;它不複製(`copy`函數除外)。 數據在任何位置可能包含空值 ("{0}"),也可能不包含。 string_view無法控制物件的存留期。 調用方有責任確保基礎字串數據有效。

可以使接受類型string_view參數的函數用於任何類似字串的類型,而不將函數製作成範本,或將函數約束到字串類型的特定子集。 唯一的要求是從字串類型到string_view存在隱式轉換。 所有標準字串類型都隱式轉換為包含相同元素類型的string_view。 換句話說,可`std::string`轉換為,`string_view`但不能轉換為`wstring_view`。

下面的範例顯示了一個非樣本函數,`f`該函數採用類型的`wstring_view`參數。 可以使用型`std::wstring`態的參數`wchar_t*`呼叫`winrt::hstring`, 與 。

```cpp
// compile with: /std:c++17
// string_view that uses elements of wchar_t
void f(wstring_view);

// pass a std::wstring:
const std::wstring& s { L"Hello" };
f(s);

// pass a C-style null-terminated string (string_view is not null-terminated):
const wchar_t* ns = L"Hello";
f(ns);

// pass a C-style character array of len characters (excluding null terminator):
const wchar_t* cs { L"Hello" };
size_t len { 5 };
f({cs,len});

// pass a WinRT string
winrt::hstring hs { L"Hello" };
f(hs);
```

## <a name="syntax"></a>語法

```cpp
template <class CharType, class Traits = char_traits<CharType>>
class basic_string_view;
```

### <a name="parameters"></a>參數

*字元類型*\
儲存在string_view中的字元的類型。 C++標準庫為此範本的專門化提供以下類型定義。

- [字元](../standard-library/string-view-typedefs.md#string_view)**型態元素**的string_view
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view) **,wchar_t**
- [char16_tu16string_view](../standard-library/string-view-typedefs.md#u16string_view) **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) **u32string_viewchar32_t。**

*性狀*\
預設值為[char_traits](char-traits-struct.md)<*字元類型*>。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_string_view](#basic_string_view)|建構空string_view,或者指向其他字串物件的全部或部分資料或 C 樣式字元陣列。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|**const_iterator**|隨機存取反覆運算器,可以讀取**const**元素。|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**反覆運算**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**指標**|`using pointer = value_type*;`|
|**參考**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>會員運算子

|運算子|描述|
|-|-|
|[運算子*](#op_eq)|將string_view或可轉換字串物件分配給另一個string_view。|
|[算子\[\]](#op_at)|傳回位於指定之索引處的元素。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[在](#at)|返回const_reference到指定位置的元素。|
|[返回](#back)|返回最後一個元素的const_reference。|
|[開始](#begin)|返回處理第一個元素的 const 反覆運算器。 (string_views是不可變的。|
|[cbegin](#cbegin)|與[開始相同](#begin)。|
|[cend](#cend)|返回指向最後一個元素的 const 反覆運算器。|
|[複製](#copy)|從源string_view索引位置到目標字元陣列的索引位置最多複製指定數量的字元。 (不推薦。 改用_Copy_s。|
|[_Copy_s](#_copy_s)|保護CRT複製功能。|
|[比較](#compare)|將string_view與指定的string_view進行比較,以確定它們是否相等,或者一個在字典中是否小於另一個。|
|[crbegin](#crbegin)|與[rbegin 相同](#rbegin)。|
|[crend](#crend)|與[rend](#rend)相同。|
|[資料](#data)|返回指向字元序列的原始非擁有指標。|
|[空](#empty)|測試string_view是否包含字元。|
|[結束](#end)|與[cend](#cend)相同。|
|[找到](#find)|以正向方向搜索與指定字元序列匹配的子字串的第一次出現。|
|[find_first_not_of](#find_first_not_of)|搜尋不是指定string_view或可轉換字串物件的任何元素的第一個字元。|
|[find_first_of](#find_first_of)|搜尋與指定string_view或可轉換字串物件的任何元素匹配的第一個字元。|
|[find_last_not_of](#find_last_not_of)|搜尋不是指定string_view或可轉換字串物件的任何元素的最後一個字元。|
|[find_last_of](#find_last_of)|搜尋作為指定string_view或可轉換字串物件元素的最後一個字元。|
|[前面](#front)|返回第一個元素的const_reference。|
|[長度](#length)|返回當前元素數。|
|[max_size](#max_size)|返回string_view可以包含的最大字元數。|
|[rbegin](#rbegin)|返回一個 const 反覆運算器,該反覆運算器處理反轉string_view中的第一個元素。|
|[remove_prefix](#remove_prefix)|按指定數量的元素向前移動指標。|
|[remove_suffix](#remove_suffix)|按從背面開始的指定元素數減小視圖的大小。|
|[rend](#rend)|返回一個 const 反覆運算器,該反覆運算器指向反轉string_view中最後一個元素的一個。|
|[rfind](#rfind)|反向搜索string_view,以尋找與指定字元序列匹配的子字串的第一次出現。|
|[大小](#size)|返回當前元素數。|
|[substr](#substr)|返回從指定索引開始的指定長度的子字串。|
|[交換](#swap)|交換兩string_views的內容。|

## <a name="remarks"></a>備註

如果要求函式產生超過 [max_size](#max_size) 個元素的序列長度，則此函式會藉由擲回 [length_error](../standard-library/length-error-class.md) 類型的物件，報告長度錯誤。

## <a name="requirements"></a>需求

[std:c++17](../build/reference/std-specify-language-standard-version.md)或更高版本

**標題:string_view>** \<

**命名空間：** std

## <a name="basic_string_viewat"></a><a name="at"></a>basic_string_view:在

在指定的 0 個索引處向字元返回const_reference。

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>參數

*抵消*\
要引用的元素的索引。

### <a name="return-value"></a>傳回值

const_reference參數索引指定位置的字元。

### <a name="remarks"></a>備註

第一個元素的索引為零,以下元素由正整數連續索引,因此長度*n* string_view具有由數位*n -* 1 索引的第*n*個元素。 **在**引發無效索引的異常,與[運算符\[](#op_at)不同。

通常,我們建議在序列**at**(`std::vector`如和 string_view 時,絕不應使用。 傳遞給序列的無效索引是應在開發過程中發現和修復的邏輯錯誤。 如果程式不能完全確定其索引是否有效,則應測試它們,而不是調用 at(),並依靠異常來防禦粗心的程式設計。

有關詳細資訊,請參閱[basic_string_view::運算子\[](#op_at)。

### <a name="example"></a>範例

```cpp
// basic_string_view_at.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>

int main()
{
    using namespace std;

    const string_view  str1("Hello world");
    string_view::const_reference refStr2 = str1.at(8); // 'r'
}
```

## <a name="basic_string_viewback"></a><a name="back"></a>basic_string_view:返回

返回最後一個元素的const_reference。

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>傳回值

const_referencestring_view中的最後一個元素。

### <a name="remarks"></a>備註

如果string_view為空,則引發異常。

請記住,在修改string_view後,例如調用`remove_suffix`,則此函數返回的元素不再是基礎數據中的最後一個元素。

### <a name="example"></a>範例

使用 C 字串文字建構的string_view不包括終止 null,因此在下面的範`back`例中傳回 p"而不是"\0"。

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

內嵌的 null 被被被被被使用的字元:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a>basic_string_view:basic_string_view

構造string_view。

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>參數

*Str*\
指向字元值的指標。

*萊恩*\
要包含在檢視中的字元數。

## <a name="remarks"></a>備註

具有 charT_ 參數的建構函數假定輸入為 null 終止,但終止空不包括在string_view中。

還可以使用文本構造string_view。 請參閱[運算符「sv」。。](string-view-operators.md#op_sv)

## <a name="basic_string_viewbegin"></a><a name="begin"></a>basic_string_view:開始

與[cbegin 相同](#cbegin)。

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>傳回值

返回定址第一個元素const_iterator。

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a>basic_string_view::cbegin

返回一個const_iterator,該const_iterator處理範圍內的第一個元素。

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

指向範圍的第一個元素或略高於空範圍末尾的位置(對於空範圍,)`cbegin() == cend()`的**const**隨機存取反覆運算器。

## <a name="basic_string_viewcend"></a><a name="cend"></a>basic_string_view::cend

返回一個const_iterator,該const_iterator位於範圍中最後一個元素之外的位置。

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>傳回值

指向範圍末尾的**集中**隨機存取反覆運算器。

### <a name="remarks"></a>備註

`cend` 所傳回的值不應該取值。

## <a name="basic_string_viewcompare"></a><a name="compare"></a>basic_string_view:比較

與指定的string_view(或可轉換字串類型)執行區分大小寫的比較,以確定兩個物件是否相等,或者一個物件在字典上是否小於另一個物件。 string_view>運算符 使用此成員函數執行比較。 [ \<](string-view-operators.md)

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>參數

*斯特夫*\
要與這種string_view相比,string_view。

*Pos*\
此string_view開始比較的索引。

*Num*\
要比較的最大字元數string_view。

*num2*\
要比較*的strv*的最大字元數。

*抵消*\
比較開始的*strv*索引。

*Ptr*\
要與此string_view比較的 C 字串。

### <a name="return-value"></a>傳回值

如果此string_view小於*strv*或*ptr,* 則為負值;如果兩個字元序列相等,則為零;或正值,如果此string_view大於*strv*或*ptr*。

### <a name="remarks"></a>備註

成員`compare`函數執行每個字元序列的全部或部分區分大小寫的比較。

### <a name="example"></a>範例

```cpp
// basic_string_view_compare.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>
#include <string>

using namespace std;

string to_alpha(int result)
{
   if (result < 0) return " less than ";
   else if (result == 0) return " equal to ";
   else return " greater than ";
}

int main()
{
   // The first member function compares
   // two string_views
   string_view sv_A("CAB");
   string_view sv_B("CAB");
   cout << "sv_A is " << sv_A << endl;
   cout << "sv_B is " << sv_B << endl;
   int comp1 = sv_A.compare(sv_B);
   cout << "sv_A is" << to_alpha(comp1) << "sv_B.\n";

   // The second member function compares part of
   // an operand string_view to another string_view
   string_view sv_C("AACAB");
   string_view sv_D("CAB");
   cout << "sv_C is: " << sv_C << endl;
   cout << "sv_D is: " << sv_D << endl;
   int comp2a = sv_C.compare(2, 3, sv_D);
   cout << "The last three characters of sv_C are"
       << to_alpha(comp2a) << "sv_D.\n";

   int comp2b = sv_C.compare(0, 3, sv_D);
   cout << "The first three characters of sv_C are"
       << to_alpha(comp2b) << "sv_D.\n";

   // The third member function compares part of
   // an operand string_view to part of another string_view
   string_view sv_E("AACAB");
   string_view sv_F("DCABD");
   cout << "sv_E: " << sv_E << endl;
   cout << "sv_F is: " << sv_F << endl;
   int comp3a = sv_E.compare(2, 3, sv_F, 1, 3);
   cout << "The three characters from position 2 of sv_E are"
       << to_alpha(comp3a)
       << "the 3 characters of sv_F from position 1.\n";

   // The fourth member function compares
   // an operand string_view to a C string
   string_view sv_G("ABC");
   const char* cs_A = "DEF";
   cout << "sv_G is: " << sv_G << endl;
   cout << "cs_A is: " << cs_A << endl;
   int comp4a = sv_G.compare(cs_A);
   cout << "sv_G is" << to_alpha(comp4a) << "cs_A.\n";

   // The fifth member function compares part of
   // an operand string_view to a C string
   string_view sv_H("AACAB");
   const char* cs_B = "CAB";
   cout << "sv_H is: " << sv_H << endl;
   cout << "cs_B is: " << cs_B << endl;
   int comp5a = sv_H.compare(2, 3, cs_B);
   cout << "The last three characters of sv_H are"
      << to_alpha(comp5a) << "cs_B.\n";

   // The sixth member function compares part of
   // an operand string_view to part of an equal length of
   // a C string
   string_view sv_I("AACAB");
   const char* cs_C = "ACAB";
   cout << "sv_I is: " << sv_I << endl;
   cout << "cs_C: " << cs_C << endl;
   int comp6a = sv_I.compare(1, 3, cs_C, 3);
   cout << "The 3 characters from position 1 of sv_I are"
      << to_alpha(comp6a) << "the first 3 characters of cs_C.\n";
}
```

```Output
sv_A is CAB
sv_B is CAB
sv_A is equal to sv_B.
sv_C is: AACAB
sv_D is: CAB
The last three characters of sv_C are equal to sv_D.
The first three characters of sv_C are less than sv_D.
sv_E: AACAB
sv_F is: DCABD
The three characters from position 2 of sv_E are equal to the 3 characters of sv_F from position 1.
sv_G is: ABC
cs_A is: DEF
sv_G is less than cs_A.
sv_H is: AACAB
cs_B is: CAB
The last three characters of sv_H are equal to cs_B.
sv_I is: AACAB
cs_C: ACAB
The 3 characters from position 1 of sv_I are equal to the first 3 characters of cs_C.
```

## <a name="basic_string_viewcopy"></a><a name="copy"></a>basic_string_view:複製

從源string_view索引位置到目標字元陣列的索引位置最多複製指定數量的字元。 我們建議您改用安全函數[basic_string_view:_Copy_s。](#_copy_s)

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*Ptr*\
要複製元素的目標字元陣列。

*計數*\
最多從源string_view複製的字元數。

*抵消*\
源中的開始位置string_view從中複製。

### <a name="return-value"></a>傳回值

實際複製的字元數。

### <a name="remarks"></a>備註

不會將 Null 字元附加至複本結尾。

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a>basic_string_view:_Copy_s

使用而不是[複製](#copy)的安全CRT複製函數。

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>參數

*dest*\
要複製元素的目標字元陣列。

*dest_size*\
*dest*的大小。

*• 計算*最多要從原始字串複製的字元數。

*_Off*\
來源字串中要建立複本的開始位置。

### <a name="return-value"></a>傳回值

實際複製的字元數。

### <a name="remarks"></a>備註

不會將 Null 字元附加至複本結尾。

有關詳細資訊,請參閱[c 運行時庫/安全功能](../c-runtime-library/security-features-in-the-crt.md)-

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a>basic_string_view:克·克貝京

返回一個const_reverse_iterator,該const_reverse_iterator處理反轉string_view中的第一個元素。

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

解決反向string_view中的第一個元素const_reverse_iterator。

## <a name="basic_string_viewcrend"></a><a name="crend"></a>basic_string_view:克倫德

與[rend](#rend)相同。

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>傳回值

返回一個const_reverse_iterator,該const_reverse_iterator處理一個經過反轉string_view末尾的一個。

## <a name="basic_string_viewdata"></a><a name="data"></a>basic_string_view::d阿塔

返回指向用於建構string_view的物件的 const 字元序列的原始非擁有指標。

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>傳回值

指向字元序列的第一個元素的指標到 const。

### <a name="remarks"></a>備註

指標無法修改字元。

string_view字元序列不一定是 null 終止的。 的`data`傳回類型不是有效的 C 字串,因為不會追加任何空字元。 空字元"\0"在類型string_view的對象中沒有特殊含義,並且可能像任何其他字元一樣是string_view物件的一部分。

## <a name="basic_string_viewempty"></a><a name="empty"></a>basic_string_view::空

測試string_view是否包含字元。

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>傳回值

如果string_view物件不包含字元,**則為 true;** 如果物件不包含字元。"string_view"物件為 true。**假**,如果它至少有一個字元。

### <a name="remarks"></a>備註

成員函數等效於[大小](#size)() = 0。

## <a name="basic_string_viewend"></a><a name="end"></a>basic_string_view:結束

返回指向最後一個元素的隨機訪問const_iterator。

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>傳回值

返回指向最後一個元素的隨機訪問const_iterator。

### <a name="remarks"></a>備註

`end`用於測試const_iterator是否已達到其string_view的末尾。 `end` 所傳回的值不應該取值。

## <a name="basic_string_viewfind"></a><a name="find"></a>basic_string_view:查找

在前進方向搜索string_view,尋找與指定字元序列匹配的字串或子字串的第一次出現。

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*Str*\
成員函數要搜索的string_view。

*chVal*\
要搜尋之成員函式的字元值。

*抵消*\
開始搜索的索引。

*Ptr*\
成員函數要為其搜索的C字串。

*計數*\
*ptr*中的字元數,從第一個字元向前計數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string_view:find_first_not_of

搜尋不是指定string_view或可轉換字串物件元素的第一個字元。

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*Str*\
成員函數要搜索的string_view。

*chVal*\
要搜尋之成員函式的字元值。

*抵消*\
開始搜索的索引。

*Ptr*\
成員函數要為其搜索的C字串。

*計數*\
成員函數要搜索的 C 字串中從第一個字元向前計數的字元數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a>basic_string_view:find_first_of

搜索與指定string_view的任何元素匹配的第一個字元。

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*chVal*\
要搜尋之成員函式的字元值。

*抵消*\
開始搜索的索引。

*Ptr*\
成員函數要為其搜索的C字串。

*計數*\
成員函數要搜索的 C 字串中從第一個字元向前計數的字元數。

*Str*\
成員函數要搜索的string_view。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string_view:find_last_not_of

搜索不是指定string_view的任何元素的最後一個字元。

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*Str*\
成員函數要搜索的string_view。

*chVal*\
要搜尋之成員函式的字元值。

*抵消*\
要完成搜索的索引。

*Ptr*\
成員函數要為其搜索的C字串。

*計數*\
從第一個字元向前計數的字元數,以*ptr*中計算。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `string_view::npos`。

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a>basic_string_view::find_last_of

搜索與指定string_view的任何元素匹配的最後一個字元。

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*Str*\
成員函數要搜索的string_view。

*chVal*\
要搜尋之成員函式的字元值。

*抵消*\
要完成搜索的索引。

*Ptr*\
成員函數要為其搜索的C字串。

*計數*\
成員函數要搜索的 C 字串中從第一個字元向前計數的字元數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的最後一個字元的索引；否則為 `npos`。

## <a name="basic_string_viewfront"></a><a name="front"></a>basic_string_view:前

返回第一個元素的const_reference。

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>傳回值

對第一個元素const_reference。

### <a name="remarks"></a>備註

如果string_view為空,則引發異常。

## <a name="basic_string_viewlength"></a><a name="length"></a>basic_string_view:長度

返回當前元素數。

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>備註

此成員函式與 [size](#size) 相同。

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a>basic_string_view::max_size

返回string_view可以包含的最大字元數。

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>傳回值

string_view可以包含的最大字元數。

### <a name="remarks"></a>備註

當操作生成長度[length_error](../standard-library/length-error-class.md)大`max_size()`於 string_view 時,將引發類型length_error的異常。

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a>basic_string_view::操作員*

將string_view或可轉換字串物件分配給另一個string_view。

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>範例

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a>basic_string_view:運算子*

提供具有指定索引的字元const_reference。

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>參數

*抵消*\
要引用的元素的索引。

### <a name="return-value"></a>傳回值

const_reference參數索引指定位置的字元。

### <a name="remarks"></a>備註

第一個元素的索引為零,以下元素由正整數連續索引,因此長度*n* string_view具有由數位*n* - 1 索引的第*n*個元素。

`operator[]`提供對string_view元素的讀取存取時,比[成員函數快](#at)。

`operator[]`不檢查作為參數傳遞的索引是否有效。 傳遞給的無效索引`operator[]`會導致未定義的行為。

如果所屬物件修改或刪除基礎字串數據,則返回的引用可能會失效。

[\_使用\_\_](../standard-library/iterator-debug-level.md)設置為 1 或 2 的 ITERATOR DEBUG LEVEL 編譯時,如果嘗試訪問string_view邊界之外的元素,則會出現運行時錯誤。 如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a>basic_string_view:rbegin

將 const 反覆運算器傳回到反轉string_view中的第一個元素。

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

將隨機存取反覆運算器傳回到反向string_view中的第一個元素,定址相應未反轉string_view中的最後一個元素。

### <a name="remarks"></a>備註

`rbegin`與反向string_view一起使用,就像[與](#begin)string_view一起使用一樣。 `rbegin`可用於向後初始化反覆運算。

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a>basic_string_view:remove_prefix

按指定數量的元素向前移動指標。

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>備註

保持不變基礎數據。 按 n 元素向前移動string_view指標,並將私`size`有 資料成員設置為大小 - n。

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a>basic_string_view:remove_suffix

按從背面開始的指定元素數減小視圖的大小。

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>備註

使基礎數據和指向它的指標保持不變。 將私有`size`資料成員設置為大小 - n。

## <a name="basic_string_viewrend"></a><a name="rend"></a>basic_string_view:rend

返回一個 const 反覆運算器,該反覆運算器指向反轉string_view中最後一個元素的一個。

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>傳回值

一個反向隨機存取反覆運算器,指向反轉string_view中最後一個元素的一個。

### <a name="remarks"></a>備註

`rend`與反向string_view一起使用,就像[端](#end)與string_view一起使用一樣。 `rend`可用於測試反向反覆運算器是否已到達其string_view的末尾。 `rend` 所傳回的值不應該取值。

## <a name="basic_string_viewrfind"></a><a name="rfind"></a>basic_string_view:如發現

反向搜索string_view,搜索與指定字元序列匹配的子字串。

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*chVal*\
要搜尋之成員函式的字元值。

*抵消*\
開始搜索的索引。

*Ptr*\
成員函數要為其搜索的C字串。

*計數*\
成員函數要搜索的 C 字串中從第一個字元向前計數的字元數。

*Str*\
成員函數要搜索的string_view。

### <a name="return-value"></a>傳回值

子字串成功時的第一個字元的索引;否則`npos`。

## <a name="basic_string_viewsize"></a><a name="size"></a>basic_string_view:大小

返回string_view中的元素數。

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>傳回值

string_view的長度。

### <a name="remarks"></a>備註

string_view可以修改其長度,例如`remove_prefix``remove_suffix`, 由於這不能修改基礎字串數據,因此string_view的大小不一定是基礎數據的大小。

## <a name="basic_string_viewsubstr"></a><a name="substr"></a>basic_string_view::子

返回表示(最多)指定位置的指定字元數string_view。

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>參數

*抵消*\
在創建副本的位置定位元素的索引,預設值為 0。

*計數*\
要包含在子字串中的字元數(如果存在)。

### <a name="return-value"></a>傳回值

表示元素的指定子序列string_view物件。

## <a name="basic_string_viewswap"></a><a name="swap"></a>basic_string_view::交換

交換兩string_views,換言之,指向基礎字串數據的指標和大小值。

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>參數

*Sv*\
源string_view其指標和大小值要與目標string_view的值交換。

## <a name="see-also"></a>另請參閱

[\<string_view>](../standard-library/string-view.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
