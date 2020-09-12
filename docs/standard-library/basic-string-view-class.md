---
title: basic_string_view 類別
description: API 參考，其參考的是 `basic_string_view` 類似 char 物件的常數連續序列。
ms.date: 9/8/2020
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::ends_with
- xstring/std::basic_string_view::starts_with
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
- std::basic_string_view, ends_with
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
- std::basic_string_view, starts_with
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 8eddf4bc6aae0338dc2e914aa57e6c1e7cc5c912
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040206"
---
# <a name="basic_string_view-class"></a>basic_string_view 類別

類別樣板 `basic_string_view<charT>` 是在 c + + 17 中加入，以安全且有效率的方式，讓函式接受各種不相關的字串類型，而不需要在這些類型上範本化函式。 類別會保存非擁有的字元資料序列的指標，以及指定序列中之字元數的長度。 無論序列是否以 null 終止，都不會進行任何假設。

標準程式庫會根據元素的類型定義數個特製化：

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

在本檔中，"string_view" 一詞通常是指任何這些 typedef。

String_view 描述讀取字串資料所需的最小通用介面。 它提供基礎資料的 const 存取;除了函數) 之外，它不會 (任何複本 `copy` 。 在任何位置，資料不一定會包含 null 值 ( ' \ 0 ' ) 。 String_view 無法控制物件的存留期。 呼叫端必須負責確保基礎字串資料有效。

接受型別 string_view 之參數的函式，可以使用任何類似字串的型別來處理，而不需要將函式放入樣板中，或將函數限制為特定的字串類型子集。 唯一的需求是從字串類型到 string_view 的隱含轉換。 所有標準字串類型都可隱含轉換成包含相同元素類型的 string_view。 換句話說， `std::string` 可以轉換成， `string_view` 而不是轉換成 `wstring_view` 。

下列範例顯示使用型別參數的非樣板函式 `f` `wstring_view` 。 您可以使用、和類型的引數來呼叫它 `std::wstring` `wchar_t*` `winrt::hstring` 。

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

*>chartype*\
String_view 中儲存的字元類型。 C + + 標準程式庫提供下列適用于此範本特殊化的 typedef。

- 針對類型的元素[string_view](../standard-library/string-view-typedefs.md#string_view)**`char`**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view)，適用于 **`wchar_t`**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view)**`char16_t`**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) **`char32_t`** 。

*性狀*\
預設為[char_traits](char-traits-struct.md) < *>chartype*>。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_string_view](#basic_string_view)|會建立空白的 string_view，或指向部分其他字串物件的資料或 C 樣式字元陣列的部分或其他部分。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|**const_iterator**|可讀取元素的隨機存取反覆運算器 **`const`** 。|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**迭 代**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**指標**|`using pointer = value_type*;`|
|**reference**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>成員運算子

|運算子|描述|
|-|-|
|[運算子 =](#op_eq)|將 string_view 或可轉換的字串物件指派給另一個 string_view。|
|[運算元\[\]](#op_at)|傳回位於指定之索引處的元素。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[at](#at)|將 const_reference 傳回至指定位置的元素。|
|[返回](#back)|傳回最後一個元素的 const_reference。|
|[開始](#begin)|傳回定址第一個元素的 const 反覆運算器。  (string_views 是不可變的。 ) |
|[cbegin](#cbegin)|與 [begin](#begin)相同。|
|[cend](#cend)|傳回指向最後一個元素之後的常數反覆運算器。|
|[copy](#copy)|從來源 string_view 中的索引位置最多將指定的字元數複製到目標字元陣列。  (不建議使用。 請改用 _Copy_s。 ) |
|[_Copy_s](#_copy_s)|安全 CRT 複製函數。|
|[比較](#compare)|將 string_view 與指定的 string_view 進行比較，以判斷它們是否相等，或詞典編纂是否小於另一個。|
|[crbegin](#crbegin)|與 [rbegin](#rbegin)相同。|
|[crend](#crend)|與 [rend](#rend)相同。|
|[data](#data)|傳回字元序列的原始非擁有指標。|
|[empty](#empty)|測試 string_view 是否包含字元。|
|[結束](#end)|與 [cend](#cend)相同。|
|[ends_with](#ends_with)<sup>c + + 20</sup>|檢查字串視圖是否以指定的尾碼結尾。|
|[find](#find)|以正向方向搜尋符合指定之字元序列的子字串第一次出現位置。|
|[find_first_not_of](#find_first_not_of)|搜尋不是指定 string_view 或可轉換的字串物件之任何元素的第一個字元。|
|[find_first_of](#find_first_of)|搜尋符合指定 string_view 或可轉換字串物件之任何元素的第一個字元。|
|[find_last_not_of](#find_last_not_of)|搜尋不是指定 string_view 或可轉換的字串物件之任何元素的最後一個字元。|
|[find_last_of](#find_last_of)|搜尋指定 string_view 或可轉換字串物件之元素的最後一個字元。|
|[前面](#front)|將 const_reference 傳回至第一個元素。|
|[length](#length)|傳回目前的元素數目。|
|[max_size](#max_size)|傳回 string_view 可以包含的字元數上限。|
|[rbegin](#rbegin)|傳回常數反覆運算器，其定址反轉 string_view 中的第一個元素。|
|[remove_prefix](#remove_prefix)|將指標向後移動指定的元素數目。|
|[remove_suffix](#remove_suffix)|將視圖的大小縮減為從後到上指定的元素數目。|
|[rend](#rend)|傳回常數反覆運算器，指向反轉 string_view 中最後一個元素之後的一個。|
|[rfind](#rfind)|針對符合指定之字元序列的子字串第一個相符專案，在反向搜尋 string_view。|
|[size](#size)|傳回目前的元素數目。|
|[starts_with](#starts_with)<sup>c + + 20</sup>|檢查字串視圖是否以指定的前置詞開頭。|
|[substr](#substr)|從指定的索引處開始，傳回指定長度的子字串。|
|[交換](#swap)|交換兩個 string_views 的內容。|

## <a name="remarks"></a>備註

如果要求函式產生超過 [max_size](#max_size) 個元素的序列長度，則此函式會藉由擲回 [length_error](../standard-library/length-error-class.md) 類型的物件，報告長度錯誤。

## <a name="requirements"></a>需求

[std： c + + 17](../build/reference/std-specify-language-standard-version.md) 或更新版本。

**標頭：**\<string_view>

**命名空間：** std

## <a name="basic_string_viewat"></a><a name="at"></a> basic_string_view：： at

將 const_reference 傳回至位於指定之以0為基礎的索引處的字元。

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>參數

*抵消*\
要參考之元素的索引。

### <a name="return-value"></a>傳回值

在參數索引所指定之位置的字元 const_reference。

### <a name="remarks"></a>備註

第一個元素的索引為零，且下列元素會以正整數連續編制索引，讓長度為 *n* 的 string_view 有 n 個第 *n*個元素，並以數位 *n-1* 來編制索引。 **在**擲回無效索引的例外狀況時，與[運算子 \[ \] ](#op_at)不同。

一般情況下，我們建議您不要使用 **的順序** ，例如 `std::vector` 和 string_view。 傳遞至序列的無效索引是在開發期間應探索和修正的邏輯錯誤。 如果程式不確定其索引是有效的，則應該進行測試，而不是在 ( # A1 的情況下呼叫，並且依賴例外狀況來防禦粗心程式設計。

如需詳細資訊，請參閱[basic_string_view：： operator \[ \] ](#op_at) 。

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

## <a name="basic_string_viewback"></a><a name="back"></a> basic_string_view：： back

傳回最後一個元素的 const_reference。

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>傳回值

Const_reference 至 string_view 中的最後一個元素。

### <a name="remarks"></a>備註

如果 string_view 是空的，則會擲回例外狀況。

請記住，在修改 string_view （例如藉由呼叫）之後，這個函式所 `remove_suffix` 傳回的元素不再是基礎資料中的最後一個元素。

### <a name="example"></a>範例

`string_view`使用 C 字串常值所建立的，不包含終止的 null。 因此，在下列範例中 `back` ， `'p'` 會傳回而不是 `'\0'` 。

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

內嵌的 null 會視為任何其他字元：

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a> basic_string_view：： basic_string_view

結構 string_view。

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>參數

*Str*\
字元值的指標。

*萊恩*\
要包含在視圖中的字元數。

### <a name="remarks"></a>備註

具有圖表 * 參數的函式會假設輸入是以 null 終止，但 string_view 中不包含終止的 null。

您也可以使用常值來建立 string_view。 請參閱 [運算子 "" sv](string-view-operators.md#op_sv)。

## <a name="basic_string_viewbegin"></a><a name="begin"></a> basic_string_view：： begin

與 [cbegin](#cbegin)相同。

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>傳回值

傳回定址第一個元素的 const_iterator。

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a> basic_string_view：： cbegin

傳回 const_iterator，以定址範圍中的第一個元素。

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

**`const`** 隨機存取反覆運算器，指向範圍的第一個元素，或指向空白範圍結尾以外的位置 (空白範圍， `cbegin() == cend()`) 。

## <a name="basic_string_viewcend"></a><a name="cend"></a> basic_string_view：： cend

傳回 const_iterator，定址範圍中最後一個元素之外的位置。

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>傳回值

**`const`** 指向範圍結尾之外的隨機存取反覆運算器。

### <a name="remarks"></a>備註

傳回的值不應取值 `cend` 。

## <a name="basic_string_viewcompare"></a><a name="compare"></a> basic_string_view：： compare

使用指定的 string_view (或可轉換的字串) 類型進行區分大小寫的比較，以判斷兩個物件是否相等，或是否詞典編纂小於另一個物件。 [ \<string_view> 運算子](string-view-operators.md)會使用這個成員函式來進行比較。

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
要與這個 string_view 比較的 string_view。

*Pos*\
此 string_view 開始比較的索引。

*Num*\
從此 string_view 要比較的最大字元數。

*num2*\
要比較的 *strv* 字元數上限。

*抵消*\
開始比較的 *strv* 索引。

*Ptr*\
要與此 string_view 比較的 C 字串。

### <a name="return-value"></a>傳回值

- 如果 `string_view` 小於*strv*或*ptr* ，則為負數值
- 如果兩個字元序列相等，則為零
- 如果這個值 `string_view` 大於*strv*或*ptr* ，則為正值

### <a name="remarks"></a>備註

`compare`成員函式會對每個字元序列的全部或部分進行區分大小寫的比較。

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

## <a name="basic_string_viewcopy"></a><a name="copy"></a> basic_string_view：： copy

從來源 string_view 中的索引位置最多將指定的字元數複製到目標字元陣列。 我們建議您改為使用安全功能 [basic_string_view：： _Copy_s](#_copy_s) 。

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*Ptr*\
要複製元素的目標字元陣列。

*計數*\
要從來源 string_view 複製的字元數。

*抵消*\
來源 string_view 中要進行複製的開始位置。

### <a name="return-value"></a>傳回值

已複製的字元數。

### <a name="remarks"></a>備註

不會將 Null 字元附加至複本結尾。

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a> basic_string_view：： _Copy_s

要使用的安全 CRT 複製函式，而不是 [複製](#copy)。

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>參數

*目標*\
要複製元素的目標字元陣列。

*dest_size*\
*目的地*的大小。

_ 從來源字串中 *算* 出要複製的字元數。

*_Off*\
來源字串中要建立複本的開始位置。

### <a name="return-value"></a>傳回值

已複製的字元數。

### <a name="remarks"></a>備註

不會將 Null 字元附加至複本結尾。

如需詳細資訊，請參閱 [c-runtime-程式庫/安全性功能-crt](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a> basic_string_view：： crbegin

傳回 const_reverse_iterator，其定址反轉 string_view 中的第一個元素。

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

Const_reverse_iterator，定址反轉 string_view 中的第一個元素。

## <a name="basic_string_viewcrend"></a><a name="crend"></a> basic_string_view：： crend

與 [rend](#rend)相同。

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>傳回值

傳回 const_reverse_iterator，其會處理反轉 string_view 結束之前的一個位址。

## <a name="basic_string_viewdata"></a><a name="data"></a> basic_string_view：:d ata

傳回原始的非擁有指標，指向用來建立 string_view 之物件的 const 字元序列。

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>傳回值

字元序列的第一個元素的指標。

### <a name="remarks"></a>備註

指標無法修改字元。

String_view 字元的序列不一定是以 null 結束。 的傳回型別 `data` 不是有效的 C 字串，因為不會附加 null 字元。 Null 字元 ' \ 0 ' 在 string_view 類型的物件中沒有特殊意義，而且可能是 string_view 物件的一部分，就像任何其他字元一樣。

## <a name="basic_string_viewempty"></a><a name="empty"></a> basic_string_view：： empty

測試 string_view 是否包含字元。

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>傳回值

**`true`** 如果 string_view 物件不包含任何字元，則為， **`false`** 如果至少有一個字元。

### <a name="remarks"></a>備註

成員函式相當於 [size](#size) ( # A1 = = 0。

## <a name="basic_string_viewend"></a><a name="end"></a> basic_string_view：： end

傳回隨機存取 const_iterator，指向最後一個專案之後的一個專案。

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>傳回值

傳回隨機存取 const_iterator，指向最後一個專案之後的一個專案。

### <a name="remarks"></a>備註

`end` 用來測試 const_iterator 是否已到達其 string_view 的結尾。 傳回的值不應取值 `end` 。

## <a name="basic_string_viewends_with"></a><a name="ends_with"></a> basic_string_view：： ends_with

檢查字串視圖是否以指定的尾碼結尾。

```cpp
bool ends_with(const CharType c) const noexcept;
bool ends_with(const CharType* const x) const noexcept;
bool ends_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>參數

*C*\
要尋找的單一字元尾碼。

*Sv*\
包含要尋找之後綴的字串視圖。 \
您可以傳遞 `std::basic_string` ，以轉換成字串的視圖。

*X*\
以 Null 結束的字元字串，其中包含要尋找的尾碼。

### <a name="return-value"></a>傳回值

`true` 如果字串視圖的結尾是指定的後置字元，則為， `false` 否則為。

### <a name="remarks"></a>備註

`ends_with()` 是 c + + 20 的新功能。 若要使用它，請指定 [/std： c + + 最新](../build/reference/std-specify-language-standard-version.md) 的編譯器選項。

請參閱 [starts_with](#starts_with) ，以檢查字串視圖是否以指定的前置詞開頭。

### <a name="example"></a>範例

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::cout << std::boolalpha; // so booleans show as 'true'/'false'  
    std::cout << std::string_view("abcdefg").ends_with('g') << '\n';
    std::cout << std::string_view("abcdefg").ends_with("eFg") << '\n';

    std::basic_string<char> str2 = "efg";
    std::cout << std::string_view("abcdefg").ends_with(str2);

    return 0;
}
```

```Output
true
false
true
```

## <a name="basic_string_viewfind"></a><a name="find"></a> basic_string_view：： find

`string_view`以正向方向搜尋符合指定字元 (s) 字元或子字串的第一次出現位置。

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*Str*\
成員函式 `string_view` 要搜尋的。

*chVal*\
要搜尋之成員函式的字元值。

*抵消*\
開始搜尋的索引。

*Ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
*Ptr*中的字元數，從第一個字元向前算起。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a> basic_string_view：： find_first_not_of

搜尋不是指定 string_view 或可轉換字串物件之元素的第一個字元。

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*Str*\
要搜尋之成員函式的 string_view。

*chVal*\
要搜尋之成員函式的字元值。

*抵消*\
開始搜尋的索引。

*Ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
要在其中搜尋成員函式的 C 字串中，從第一個字元向前算起的字元數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a> basic_string_view：： find_first_of

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

*抵消*\
開始搜尋的索引。

*Ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
要在其中搜尋成員函式的 C 字串中，從第一個字元向前算起的字元數。

*Str*\
要搜尋之成員函式的 string_view。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a> basic_string_view：： find_last_not_of

搜尋不是指定 string_view 之任何元素的最後一個字元。

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*Str*\
要搜尋之成員函式的 string_view。

*chVal*\
要搜尋之成員函式的字元值。

*抵消*\
要在其上完成搜尋的索引。

*Ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
從 *ptr*中的第一個字元開始算起的字元數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `string_view::npos`。

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a> basic_string_view：： find_last_of

搜尋符合指定 string_view 之任何元素的最後一個字元。

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*Str*\
要搜尋之成員函式的 string_view。

*chVal*\
要搜尋之成員函式的字元值。

*抵消*\
要在其上完成搜尋的索引。

*Ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
要在其中搜尋成員函式的 C 字串中，從第一個字元向前算起的字元數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的最後一個字元的索引；否則為 `npos`。

## <a name="basic_string_viewfront"></a><a name="front"></a> basic_string_view：： front

將 const_reference 傳回至第一個元素。

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>傳回值

第一個元素的 const_reference。

### <a name="remarks"></a>備註

如果 string_view 是空的，則會擲回例外狀況。

## <a name="basic_string_viewlength"></a><a name="length"></a> basic_string_view：： length

傳回目前的元素數目。

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>備註

此成員函式與 [size](#size) 相同。

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a> basic_string_view：： max_size

傳回 string_view 可以包含的字元數上限。

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>傳回值

String_view 可以包含的字元數上限。

### <a name="remarks"></a>備註

當作業產生長度大於的 string_view 時，會擲回類型 [length_error](../standard-library/length-error-class.md) 的例外狀況 `max_size()` 。

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a> basic_string_view：： operator =

將 string_view 或可轉換的字串物件指派給另一個 string_view。

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>範例

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a> basic_string_view：： operator []

提供具有指定索引之字元的 const_reference。

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>參數

*抵消*\
要參考之元素的索引。

### <a name="return-value"></a>傳回值

在參數索引所指定之位置的字元 const_reference。

### <a name="remarks"></a>備註

第一個元素的索引為零，且下列元素會以正整數連續編制索引，讓長度為 *n* 的 string_view 有 n 個第 *n*個元素，並以數位 *n-1* 來編制索引。

`operator[]` 會比的成員函式更快 [，以提供](#at) string_view 之元素的讀取權限。

`operator[]` 不會檢查做為引數傳遞的索引是否有效。 傳遞了不正確索引， `operator[]` 導致未定義的行為。

如果擁有物件修改或刪除基礎字串資料，傳回的參考可能會失效。

當您將[ \_ 反覆運算器的 \_ 調試 \_ 層級](../standard-library/iterator-debug-level.md)設定為1或2時，如果您嘗試存取 string_view 範圍以外的專案，就會發生執行階段錯誤。 如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a> basic_string_view：： rbegin

將常數反覆運算器傳回至反向 string_view 中的第一個元素。

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

傳回反向 string_view 中第一個專案的隨機存取反覆運算器，定址對應未反轉 string_view 中的最後一個元素。

### <a name="remarks"></a>備註

`rbegin` 與反向 string_view 搭配使用，就如同 [開始](#begin) 與 string_view 搭配使用一樣。 `rbegin` 可以用來將反復專案初始化。

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a> basic_string_view：： remove_prefix

將指標向後移動指定的元素數目。

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>備註

讓基礎資料保持不變。 將 string_view 指標向前移動 n 個元素，並將私用 `size` 資料成員設為大小-n。

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a> basic_string_view：： remove_suffix

將視圖的大小縮減為從後到上指定的元素數目。

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>備註

將基礎資料和指標保持不變。 將私用 `size` 資料成員設定為大小-n。

## <a name="basic_string_viewrend"></a><a name="rend"></a> basic_string_view：： rend

傳回常數反覆運算器，指向反轉 string_view 中最後一個元素之後的一個。

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>傳回值

常數反向隨機存取反覆運算器，指向反轉 string_view 中最後一個元素之後的一個。

### <a name="remarks"></a>備註

`rend` 與反向 string_view 搭配使用，就如同 [end](#end) 用於 string_view。 `rend` 可以用來測試反向反覆運算器是否已到達其 string_view 的結尾。 傳回的值不應取值 `rend` 。

## <a name="basic_string_viewrfind"></a><a name="rfind"></a> basic_string_view：： rfind

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

*抵消*\
開始搜尋的索引。

*Ptr*\
要搜尋之成員函式的 C 字串。

*計數*\
要在其中搜尋成員函式的 C 字串中，從第一個字元向前算起的字元數。

*Str*\
要搜尋之成員函式的 string_view。

### <a name="return-value"></a>傳回值

成功時，子字串第一個字元的索引;否則為 `npos` 。

## <a name="basic_string_viewsize"></a><a name="size"></a> basic_string_view：： size

傳回 string_view 中的元素數目。

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>傳回值

String_view 的長度。

### <a name="remarks"></a>備註

String_view 可以修改其長度，例如， `remove_prefix` 和 `remove_suffix` 。 由於這不會修改基礎字串資料，因此 string_view 的大小不一定是基礎資料的大小。

## <a name="basic_string_viewstarts_with"></a><a name="starts_with"></a> basic_string_view：： starts_with

檢查字串視圖是否以指定的前置詞開頭。

```cpp
bool starts_with(const CharType c) const noexcept;
bool starts_with(const CharType* const x) const noexcept;
bool starts_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>參數

*C*\
要尋找的單一字元前置詞。

*Sv*\
字串視圖，包含要尋找的前置詞。 \
您可以傳遞 `std::basic_string` ，以轉換成字串的視圖。

*X*\
以 Null 結束的字元字串，其中包含要尋找的前置詞。

### <a name="return-value"></a>傳回值

`true` 如果字串開頭為指定的前置詞，則為， `false` 否則為。

### <a name="remarks"></a>備註

`starts_with()` 是 c + + 20 的新功能。 若要使用它，請指定 [/std： c + + 最新](../build/reference/std-specify-language-standard-version.md) 的編譯器選項。

請參閱 [ends_with](#ends_with) ，以查看字串是否以後綴結尾。

### <a name="example"></a>範例

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::cout << std::boolalpha; // so booleans show as 'true'/'false'  
    std::cout << std::string_view("abcdefg").starts_with('b') << '\n';
    std::cout << std::string_view("abcdefg").starts_with("aBc") << '\n';

    std::basic_string<char> str2 = "abc";
    std::cout << std::string_view("abcdefg").starts_with(str2);

    return 0;
}
```

```Output
false
false
true
```

## <a name="basic_string_viewsubstr"></a><a name="substr"></a> basic_string_view：： substr

傳回 string_view，表示從指定位置到最) 指定字元數的 (。

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>參數

*抵消*\
索引，可在建立複本的位置尋找元素，預設值為0。

*計數*\
子字串中要包含的字元數（如果有的話）。

### <a name="return-value"></a>傳回值

String_view 物件，代表指定的元素子序列。

## <a name="basic_string_viewswap"></a><a name="swap"></a> basic_string_view：： swap

交換兩個 string_views，亦即基礎字串資料的指標和大小值。

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>參數

*Sv*\
其指標和大小值要與目的地 string_view 交換的來源 string_view。

## <a name="see-also"></a>另請參閱

[\<string_view>](../standard-library/string-view.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
