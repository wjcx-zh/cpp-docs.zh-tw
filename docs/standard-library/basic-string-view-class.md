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
ms.openlocfilehash: 8f6b1bdf5648298221a8b41de31ec49ae0c47513
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076721"
---
# <a name="basic_string_view-class"></a>basic_string_view 類別

類別樣板 `basic_string_view<charT>` 是在 c + + 17 中加入，可作為函式接受各種不相關字串類型的安全且有效率的方式，而不需要在這些類型上範本化函數。 類別會將非擁有指標保存在連續的字元資料序列中，而長度則會指定序列中的字元數。 對於序列是否以 null 終止而言，不會進行任何假設。

標準程式庫會根據元素的類型，定義數個特製化：

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

在本檔中，「string_view」一詞通常是指其中任何一個 typedef。

String_view 描述讀取字串資料所需的最小通用介面。 它提供基礎資料的 const 存取;它不會進行任何複製（`copy` 函式除外）。 資料不一定會在任何位置包含 null 值（' \ 0 '）。 String_view 無法控制物件的存留期。 呼叫者必須負責確保基礎字串資料有效。

接受類型 string_view 參數的函式可以用來處理任何類似字串的類型，而不需要將函式放入範本中，或將函式限制為特定的字串類型子集。 唯一的要求是從字串類型到 string_view 都有隱含轉換。 所有標準字串類型都可以隱含地轉換成包含相同專案類型的 string_view。 換句話說，`std::string` 可以轉換成 `string_view` 而不是 `wstring_view`。

下列範例顯示使用 `wstring_view`型別參數的非樣板函式 `f`。 您可以使用 `std::wstring`、`wchar_t*`和 `winrt::hstring`類型的引數來呼叫它。

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

*CharType*\
儲存在 string_view 中的字元類型。 C++標準程式庫會針對此範本的特製化提供下列 typedef。
- [string_view](../standard-library/string-view-typedefs.md#string_view)類型為**char**的元素
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view)，適用于**wchar_t**
- **char16_t**的[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)
- **char32_t**的[u32string_view](../standard-library/string-view-typedefs.md#u32string_view) 。

*特性*\
預設為[char_traits](char-traits-struct.md)<*CharType*>。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_string_view](#basic_string_view)|會建立空的 string_view，或是指向部分其他字串物件資料或 C 樣式字元陣列的全部或部分。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|**const_iterator**|可讀取**const**元素的隨機存取反覆運算器。|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**iterator**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**pointer**|`using pointer = value_type*;`|
|**reference**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>成員運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|將 string_view 或可轉換的字串物件指派給另一個 string_view。|
|[operator\[\]](#op_at)|傳回位於指定之索引處的元素。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[at](#at)|傳回指定位置的元素 const_reference。|
|[back](#back)|傳回最後一個元素的 const_reference。|
|[begin](#begin)|傳回定址第一個元素的 const 反覆運算器。 （string_views 不變）。|
|[cbegin](#cbegin)|與 [[開始](#begin)] 相同。|
|[cend](#cend)|傳回指向最後一個元素之後的常數反覆運算器。|
|[copy](#copy)|從來源 string_view 中的索引位置，最多將指定的字元數複製到目標字元陣列。 （不建議使用。 請改用 _Copy_s）。|
|[_Copy_s](#_copy_s)|保護 CRT 複製函式。|
|[compare](#compare)|比較 string_view 與指定的 string_view，判斷它們是否相等，或詞典編纂是否小於另一個。|
|[crbegin](#crbegin)|與[rbegin](#rbegin)相同。|
|[crend](#crend)|與[rend](#rend)相同。|
|[data](#data)|將未經處理的非擁有指標傳回字元序列。|
|[empty](#empty)|測試 string_view 是否包含字元。|
|[end](#end)|與[cend](#cend)相同。|
|[find](#find)|以正向方向搜尋符合指定之字元序列的子字串第一次出現。|
|[find_first_not_of](#find_first_not_of)|搜尋不是指定 string_view 或可轉換字串物件之任何元素的第一個字元。|
|[find_first_of](#find_first_of)|搜尋符合指定 string_view 或可轉換字串物件之任何元素的第一個字元。|
|[find_last_not_of](#find_last_not_of)|搜尋不是指定 string_view 或可轉換字串物件之任何元素的最後一個字元。|
|[find_last_of](#find_last_of)|搜尋屬於指定 string_view 或可轉換字串物件之元素的最後一個字元。|
|[front](#front)|傳回第一個元素的 const_reference。|
|[length](#length)|傳回目前的元素數目。|
|[max_size](#max_size)|傳回 string_view 可以包含的最大字元數。|
|[rbegin](#rbegin)|傳回常數反覆運算器，定址為反轉 string_view 中的第一個元素。|
|[remove_prefix](#remove_prefix)|將指標往前移動指定的專案數。|
|[remove_suffix](#remove_suffix)|根據從後開始的指定元素數目，減少視圖的大小。|
|[rend](#rend)|傳回常數反覆運算器，指向反轉 string_view 中最後一個元素之後的一個。|
|[rfind](#rfind)|針對第一次出現的子字串（符合指定的字元序列）進行反向搜尋 string_view。|
|[size](#size)|傳回目前的元素數目。|
|[substr](#substr)|從指定的索引開始，傳回指定之長度的子字串。|
|[swap](#swap)|交換兩個 string_views 的內容。|

## <a name="remarks"></a>備註

如果要求函式產生超過 [max_size](#max_size) 個元素的序列長度，則此函式會藉由擲回 [length_error](../standard-library/length-error-class.md) 類型的物件，報告長度錯誤。

## <a name="requirements"></a>需求

[std： c + + 17](../build/reference/std-specify-language-standard-version.md)或更新版本

**標頭：** \<string_view >

**命名空間:** std

## <a name="basic_string_viewat"></a><a name="at"></a>basic_string_view：： at

傳回指定之以零為起始之索引處的字元 const_reference。

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>參數

*位移*\
要參考之元素的索引。

### <a name="return-value"></a>傳回值

參數索引所指定之位置的字元 const_reference。

### <a name="remarks"></a>備註

第一個元素的索引為零，且下列專案是以正整數連續編制索引，因此長度為*n*的 string_view 有第*n*個元素，以數位*n-* 1 來編制索引。 發生不正確索引**時**，會擲回例外狀況，而不像[operator\[\]](#op_at)。

一般來說，我們建議您不要使用 `std::vector` 和 string_view**之類的序列**。 傳遞至序列的無效索引是應該在開發期間探索和修正的邏輯錯誤。 如果程式並不確定其索引是有效的，則應該測試它們，而不是呼叫（），並且依賴例外狀況來防禦粗心程式設計。

如需詳細資訊，請參閱[basic_string_view：： operator\[\]](#op_at) 。

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

## <a name="basic_string_viewback"></a><a name="back"></a>basic_string_view：： back

傳回最後一個元素的 const_reference。

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>傳回值

String_view 中最後一個元素的 const_reference。

### <a name="remarks"></a>備註

如果 string_view 是空的，則擲回例外狀況。

請記住，修改 string_view 後（例如藉由呼叫 `remove_suffix`），此函式所傳回的元素不再是基礎資料中的最後一個元素。

### <a name="example"></a>範例

使用 C 字串常值所建立的 string_view 不包含終止的 null，因此在下列範例中 `back` 會傳回 ' p ' 而非 ' \ 0 '。

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

內嵌的 null 會被視為任何其他字元：

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a>basic_string_view：： basic_string_view

構造 string_view。

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>參數

*str*\
字元值的指標。

*len*\
要包含在此視圖中的字元數。

## <a name="remarks"></a>備註

具有圖表 * 參數的函式會假設輸入是以 null 結束，但終止的 null 不會包含在 string_view 中。

您也可以使用常值來建立 string_view。 請參閱[operator "" sv](string-view-operators.md#op_sv)。

## <a name="basic_string_viewbegin"></a><a name="begin"></a>basic_string_view：： begin

與[cbegin](#cbegin)相同。

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>傳回值
傳回定址第一個元素的 const_iterator。

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a>basic_string_view：： cbegin

傳回定址範圍中第一個元素的 const_iterator。

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

**常數**隨機存取反覆運算器，指向範圍的第一個專案，或指向空白範圍結尾之外的位置（針對空白範圍，`cbegin() == cend()`）。

## <a name="basic_string_viewcend"></a><a name="cend"></a>basic_string_view：： cend

傳回 const_iterator，其定址範圍中最後一個元素之後的位置。

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>傳回值

**常數**隨機存取反覆運算器，指向超出範圍的結尾。

### <a name="remarks"></a>備註

`cend` 所傳回的值不應該取值。

## <a name="basic_string_viewcompare"></a><a name="compare"></a>basic_string_view：： compare

執行區分大小寫的比較與指定的 string_view （或可轉換的字串類型），以判斷兩個物件是否相等，或詞典編纂是否小於另一個。 [\<string_view > 運算子](string-view-operators.md)會使用此成員函式來執行比較。

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>參數

*strv*\
要與此 string_view 比較的 string_view。

*pos*\
此 string_view 的索引，這是比較開始的位置。

*num*\
此 string_view 中要比較的最大字元數。

*num2*\
要比較之*strv*中的最大字元數。

*位移*\
開始比較的*strv*索引。

*ptr*\
要與這個 string_view 比較的 C 字串。

### <a name="return-value"></a>傳回值

如果這個 string_view 小於*strv*或*ptr*，則為負值;如果兩個字元序列相等，則為零。如果這個 string_view 大於*strv*或*ptr*，則為正數值。

### <a name="remarks"></a>備註

`compare` 成員函式會對每個字元序列的全部或部分執行區分大小寫的比較。

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

## <a name="basic_string_viewcopy"></a><a name="copy"></a>basic_string_view：： copy

從來源 string_view 中的索引位置，最多將指定的字元數複製到目標字元陣列。 我們建議您改用安全函數[basic_string_view：： _Copy_s](#_copy_s) 。

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*ptr*\
要複製元素的目標字元陣列。

*計數*\
要從來源 string_view 複製的字元數。

*位移*\
來源 string_view 中要從中進行複製的開始位置。

### <a name="return-value"></a>傳回值

實際複製的字元數。

### <a name="remarks"></a>備註

不會將 Null 字元附加至複本結尾。

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a>basic_string_view：： _Copy_s

要使用的安全 CRT 複製函式，而不是[複製](#copy)。

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>參數

*目的地*\
要複製元素的目標字元陣列。

*dest_size*\
*目標*的大小。

_*計算*從來源字串複製的字元數上限。

*_Off*\
來源字串中要建立複本的開始位置。

### <a name="return-value"></a>傳回值

實際複製的字元數。

### <a name="remarks"></a>備註

不會將 Null 字元附加至複本結尾。

如需詳細資訊，請參閱[c-執行時間程式庫/安全性-crt 中的功能](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a>basic_string_view：： crbegin

傳回 const_reverse_iterator，其定址反轉 string_view 中的第一個元素。

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

Const_reverse_iterator，定址反轉 string_view 中的第一個元素。

## <a name="basic_string_viewcrend"></a><a name="crend"></a>basic_string_view：： crend

與[rend](#rend)相同。

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>傳回值

傳回 const_reverse_iterator，其定址反轉 string_view 結尾的一個。

## <a name="basic_string_viewdata"></a><a name="data"></a>basic_string_view：:d ata

將未經處理的非擁有指標傳回給用來結構化 string_view 之物件的 const 字元序列。

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>傳回值

字元序列的第一個元素的指標。

### <a name="remarks"></a>備註

指標無法修改字元。

String_view 字元的順序不一定是以 null 結束。 `data` 的傳回型別不是有效的 C 字串，因為不會附加 null 字元。 Null 字元 ' \ 0 ' 在類型 string_view 的物件中沒有特殊意義，而且可能是 string_view 物件的一部分，就像任何其他字元一樣。

## <a name="basic_string_viewempty"></a><a name="empty"></a>basic_string_view：： empty

測試 string_view 是否包含字元。

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>傳回值

如果 string_view 物件未包含任何字元，則為**true** ;如果至少有一個字元，則**為 false** 。

### <a name="remarks"></a>備註

成員函式相當於[size](#size)（） = = 0。

## <a name="basic_string_viewend"></a><a name="end"></a>basic_string_view：： end

傳回隨機存取 const_iterator，指向最後一個元素之後的一個。

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>傳回值

傳回隨機存取 const_iterator，指向最後一個元素之後的一個。

### <a name="remarks"></a>備註

`end` 可用來測試 const_iterator 是否已達到其 string_view 的結尾。 `end` 所傳回的值不應該取值。

## <a name="basic_string_viewfind"></a><a name="find"></a>basic_string_view：： find

在 string_view 的正向方向搜尋符合指定之字元序列的第一次出現的字元或子字串。

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*str*\
要搜尋之成員函式的 string_view。

*chVal*\
要搜尋之成員函式的字元值。

*位移*\
開始搜尋的索引。

*ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
*Ptr*中的字元數，從第一個字元向前計數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string_view：： find_first_not_of

搜尋不是指定 string_view 或可轉換字串物件之元素的第一個字元。

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*str*\
要搜尋之成員函式的 string_view。

*chVal*\
要搜尋之成員函式的字元值。

*位移*\
開始搜尋的索引。

*ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
要在其中搜尋成員函式的 C 字串中，從第一個字元向前計數的字元數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a>basic_string_view：： find_first_of

搜尋符合指定 string_view 之任何元素的第一個字元。

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*chVal*\
要搜尋之成員函式的字元值。

*位移*\
開始搜尋的索引。

*ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
要在其中搜尋成員函式的 C 字串中，從第一個字元向前計數的字元數。

*str*\
要搜尋之成員函式的 string_view。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string_view：： find_last_not_of

搜尋不是指定 string_view 之任何元素的最後一個字元。

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*str*\
要搜尋之成員函式的 string_view。

*chVal*\
要搜尋之成員函式的字元值。

*位移*\
要完成搜尋的索引。

*ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
*Ptr*中的字元數，從第一個字元向前計數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `string_view::npos`。

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a>basic_string_view：： find_last_of

搜尋符合指定 string_view 之任何元素的最後一個字元。

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*str*\
要搜尋之成員函式的 string_view。

*chVal*\
要搜尋之成員函式的字元值。

*位移*\
要完成搜尋的索引。

*ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
要在其中搜尋成員函式的 C 字串中，從第一個字元向前計數的字元數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的最後一個字元的索引；否則為 `npos`。

## <a name="basic_string_viewfront"></a><a name="front"></a>basic_string_view：： front

傳回第一個元素的 const_reference。

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>傳回值

第一個元素的 const_reference。

### <a name="remarks"></a>備註

如果 string_view 是空的，則擲回例外狀況。

## <a name="basic_string_viewlength"></a><a name="length"></a>basic_string_view：： length

傳回目前的元素數目。

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>備註

此成員函式與 [size](#size) 相同。

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a>basic_string_view：： max_size

傳回 string_view 可以包含的最大字元數。

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>傳回值

String_view 可以包含的最大字元數。

### <a name="remarks"></a>備註

當作業產生的 string_view 長度大於 `max_size()`時，就會擲回類型[length_error](../standard-library/length-error-class.md)的例外狀況。

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a>basic_string_view：： operator =

將 string_view 或可轉換的字串物件指派給另一個 string_view。

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>範例

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a>basic_string_view：： operator []

提供具有指定索引之字元的 const_reference。

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>參數

*位移*\
要參考之元素的索引。

### <a name="return-value"></a>傳回值

參數索引所指定之位置的字元 const_reference。

### <a name="remarks"></a>備註

第一個元素的索引為零，且下列專案是以正整數連續編制索引，因此長度為*n*的 string_view 有第*n*個元素，以數位*n* -1 來編制索引。

`operator[]`[比的成員](#at)函式更快，可提供 string_view 元素的讀取權限。

`operator[]` 不會檢查當做引數傳遞的索引是否有效。 傳遞給 `operator[]` 的無效索引會導致未定義的行為。

如果由擁有物件修改或刪除基礎字串資料，傳回的參考可能會無效。

使用\_ITERATOR 進行編譯時[\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)設為1或2時，如果您嘗試存取 string_view 界限以外的專案，就會發生執行階段錯誤。 如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md)。

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a>basic_string_view：： rbegin

將常數反覆運算器傳回至反向 string_view 中的第一個元素。

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

傳回反轉 string_view 中第一個專案的隨機存取反覆運算器，其定址是對應的未反轉 string_view 中的最後一個元素。

### <a name="remarks"></a>備註

`rbegin` 是與反轉的 string_view 搭配使用，就如同[begin](#begin)是與 string_view 搭配使用一樣。 `rbegin` 可以用來向後初始化反復專案。

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a>basic_string_view：： remove_prefix

將指標往前移動指定的專案數。

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>備註

將基礎資料保持不變。 將 string_view 指標向前移動 n 個元素，並將私用 `size` 資料成員設定為大小-n。

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a>basic_string_view：： remove_suffix

根據從後開始的指定元素數目，減少視圖的大小。

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>備註

將基礎資料和指標保持不變。 將私用 `size` 資料成員設定為大小-n。

## <a name="basic_string_viewrend"></a><a name="rend"></a>basic_string_view：： rend

傳回常數反覆運算器，指向反轉 string_view 中最後一個元素之後的一個。

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>傳回值

Const 反向隨機存取反覆運算器，指向反轉 string_view 中最後一個元素之後的一個。

### <a name="remarks"></a>備註

`rend` 會與反轉的 string_view 搭配使用，就如同[end](#end)是與 string_view 搭配使用一樣。 `rend` 可以用來測試反向反覆運算器是否已到達其 string_view 的結尾。 `rend` 所傳回的值不應該取值。

## <a name="basic_string_viewrfind"></a><a name="rfind"></a>basic_string_view：： rfind

針對符合指定之字元序列的子字串，反向搜尋 string_view。

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*chVal*\
要搜尋之成員函式的字元值。

*位移*\
開始搜尋的索引。

*ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
要在其中搜尋成員函式的 C 字串中，從第一個字元向前計數的字元數。

*str*\
要搜尋之成員函式的 string_view。

### <a name="return-value"></a>傳回值

成功時，子字串的第一個字元的索引。否則 `npos`。

## <a name="basic_string_viewsize"></a><a name="size"></a>basic_string_view：： size

傳回 string_view 中的元素數目。

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>傳回值

String_view 的長度。

### <a name="remarks"></a>備註

String_view 可以修改其長度，例如，`remove_prefix` 和 `remove_suffix`。 因為這不會修改基礎字串資料，string_view 的大小不一定是基礎資料的大小。

## <a name="basic_string_viewsubstr"></a><a name="substr"></a>basic_string_view：： substr

傳回 string_view，代表指定位置中指定的字元數（最多）。

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>參數

*位移*\
在建立複本的位置上尋找專案的索引，預設值為0。

*計數*\
要包含在子字串中的字元數（如果有的話）。

### <a name="return-value"></a>傳回值

String_view 物件，表示指定的元素子序列。

## <a name="basic_string_viewswap"></a><a name="swap"></a>basic_string_view：： swap

交換兩個 string_views，換言之，也就是基礎字串資料的指標和大小的值。

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>參數

*sv*\
要與目的地 string_view 交換其指標和大小值的來源 string_view。

## <a name="see-also"></a>另請參閱

[\<string_view >](../standard-library/string-view.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
