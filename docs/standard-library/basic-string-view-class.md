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
ms.openlocfilehash: 0ac5e3d528881f7b1caa0a1dcdae0161a6777e57
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346936"
---
# <a name="basicstringview-class"></a>basic_string_view 類別

類別樣板`basic_string_view<charT>`已新增在 c++17 中做為安全且有效率的方式，以接受各種函式不相關而不需要在這些類型要範本化函式的字串型別。 類別會保存非主控指標連續的一連串字元資料，並在序列中指定的字元數的長度。 相對於序列是否是以 null 結尾，不會做任何假設。

標準程式庫定義數個項目的類型為基礎的特製化：

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

本文件中，「 string_view 」 一詞是指通常任何這些 typedef。

String_view 說明讀取字串資料所需的最小通用介面。 它提供 const 存取基礎資料;它會製作任何複本 (除了`copy`函式)。 可能的資料，或不能包含 null 值 ('\0') 的任何位置。 String_view 有無法控制物件的存留期。 是呼叫者的責任，以確保基礎字串資料有效。

搭配任何類似字串的類型，而不需要進行函式到範本中，或限制對特定子集的字串類型的函式可接受之參數的型別 string_view 的函式。 唯一的需求是隱含的轉換存在從字串型別至 string_view。 所有的標準字串類型會隱含地轉換成包含相同的項目型別 string_view。 亦即`std::string`轉換成`string_view`而無法供`wstring_view`。

下列範例示範 jinou než funkci š`f`採用參數的型別`wstring_view`。 它可以使用的型別引數呼叫`std::wstring`， `wchar_t*`，和`winrt::hstring`。

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

*CharType*<br/>
而儲存在 string_view 的字元類型。 C++標準程式庫提供下列 typedef 的這個樣板的特製化。
- [string_view](../standard-library/string-view-typedefs.md#string_view)類型的項目**char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view)，如**wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) for **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) for **char32_t**。

*特性*<br/>
預設值為[char_traits](char-traits-struct.md)<*CharType*>。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_string_view](#basic_string_view)|建構 string_view，是空的否則指向全部或部分的其他字串物件的資料，或 C 樣式字元陣列。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|**const_iterator**|隨機存取迭代器可以讀取**const**項目。|
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
|[operator=](#op_eq)|給另一個 string_view string_view 或轉換的字串物件。|
|[operator\[\]](#op_at)|傳回位於指定之索引處的元素。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[at](#at)|傳回指定位置的項目 const_reference。|
|[back](#back)|Const_reference 傳回最後一個項目。|
|[begin](#begin)|傳回 const 迭代器定址的第一個元素。 （string_views 是不可變的）。|
|[cbegin](#cbegin)|與相同[開始](#begin)。|
|[cend](#cend)|傳回 const 迭代器，指向最後一個元素的其中一個。|
|[copy](#copy)|最多指定的數目的字元複製從來源 string_view 中的索引位置到目標字元陣列。 （不建議使用。 請改用 _Copy_s。）|
|[_Copy_s](#_copy_s)|安全的 CRT 複本函式。|
|[compare](#compare)|比較使用指定的 string_view 以判斷它們是否相等，或者其中一個詞典編纂上小於另 string_view。|
|[crbegin](#crbegin)|與相同[rbegin](#rbegin)。|
|[crend](#crend)|與相同[rend](#rend)。|
|[data](#data)|傳回未經處理的非主控指標的字元序列。|
|[empty](#empty)|測試是否 string_view 包含的字元。|
|[end](#end)|與相同[cend](#cend)。|
|[find](#find)|第一次出現之符合指定的一連串字元的子字串以正向方向搜尋。|
|[find_first_not_of](#find_first_not_of)|搜尋不是指定的 string_view 或轉換的字串物件的任何元素的第一個字元。|
|[find_first_of](#find_first_of)|搜尋符合指定的 string_view 或轉換的字串物件的任何元素的第一個字元。|
|[find_last_not_of](#find_last_not_of)|不是指定的 string_view 或轉換的字串物件的任何元素的最後一個字元的搜尋。|
|[find_last_of](#find_last_of)|搜尋為指定的 string_view 或轉換的字串物件的項目最後一個字元。|
|[front](#front)|Const_reference 回到第一個項目。|
|[length](#length)|傳回目前的元素數目。|
|[max_size](#max_size)|傳回 string_view 也可能包含的字元的數上限。|
|[rbegin](#rbegin)|傳回定址反轉 string_view 中的第一個元素的 const 迭代器。|
|[remove_prefix](#remove_prefix)|將指標向前移所指定的元素數目。|
|[remove_suffix](#remove_suffix)|檢視的大小減少為指定數目的項目從 [上一步]。|
|[rend](#rend)|傳回常數迭代器，指向一個反向的 string_view 中最後一個元素。|
|[rfind](#rfind)|搜尋 string_view 反向第一個出現之符合指定的一連串字元的子字串。|
|[size](#size)|傳回目前的元素數目。|
|[substr](#substr)|傳回指定索引處開始的指定長度的子字串。|
|[swap](#swap)|交換兩個 string_views 的內容。|

## <a name="remarks"></a>備註

如果要求函式產生超過 [max_size](#max_size) 個元素的序列長度，則此函式會藉由擲回 [length_error](../standard-library/length-error-class.md) 類型的物件，報告長度錯誤。

## <a name="requirements"></a>需求

[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)或更新版本

**標頭：** \<string_view >

**命名空間：** std

## <a name="at"></a>  basic_string_view::at

Const_reference 回到指定 0 為基底的索引處的字元。

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>參數

*offset*<br/>
要參考之項目的索引。

### <a name="return-value"></a>傳回值

Const_reference 至指定的參數索引位置處的字元。

### <a name="remarks"></a>備註

第一個元素的索引為零，而且會以正整數，會對連續索引下列項目，讓長度的 string_view *n*已*n*數個項目編製索引*n-* 1。 **在**不同於擲回的例外狀況，無效的索引，如[運算子\[\]](#op_at)。 

一般情況下，我們建議**位於**這類的序列 (sequence)`std::vector`和 string_view 應該永遠不會使用。 傳遞至序列的無效索引是應該會發現並修正在開發期間的邏輯錯誤。 如果程式未完全可以確定其索引皆有效，它應該進行測試、 未呼叫 at() 和例外狀況來防禦粗心的程式設計。

請參閱[basic_string_view::operator\[ \] ](#op_at)如需詳細資訊。

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

## <a name="back"></a>  basic_string_view::back

Const_reference 傳回最後一個項目。

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>傳回值

Const_reference string_view 中的最後一個元素。

### <a name="remarks"></a>備註

如果是空的 string_view，則會擲回例外狀況。

請記住，string_view 經過修改之後，例如藉由呼叫`remove_suffix`，則此函式所傳回的項目不會再為基礎的資料中的最後一個元素。

### <a name="example"></a>範例

C 字串常值來建構 string_view 不包含終止的 null，因此在下列範例中`back`傳回 'p' 並不是 '\0'。

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p 
```

內嵌的 null 會視為其他任何字元：

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_view"></a>  basic_string_view::basic_string_view

建構 string_view。

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>參數

*str*<br/>
字元值的指標。

*len*<br/>
要包含在檢視中的字元數。

## <a name="remarks"></a>備註

圖表 * 參數的建構函式會假設輸入是以 null 終止，但結束的 null 不會納入 string_view。

您也可以建構 string_view 具有常值。 請參閱[運算子""sv](string-view-operators.md#op_sv)。

## <a name="begin"></a>  basic_string_view::begin

與相同[cbegin](#cbegin)。

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>傳回值
傳回的第一個項目定址的 const_iterator。

## <a name="cbegin"></a>  basic_string_view::cbegin

傳回範圍中的第一個項目定址的 const_iterator。

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

A **const**隨機存取迭代器指向第一個項目範圍或只是空白範圍結尾之外的位置 (空白範圍， `cbegin() == cend()`)。

## <a name="cend"></a>  basic_string_view::cend

傳回定址之外的範圍中的最後一個元素位置的 const_iterator。

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>傳回值

A **const**指向範圍結尾之外的隨機存取迭代器。

### <a name="remarks"></a>備註

`cend` 所傳回的值不應該取值。

## <a name="compare"></a> basic_string_view::compare

執行區分大小寫比較以判斷兩個物件是否相等，或者其中一個詞典編纂上小於另指定的 string_view> （或轉換的字串類型）。 [ \<String_view > 運算子](string-view-operators.md)使用此成員函式來執行比較。

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>參數

*strv*<br/>
要比較以這個 string_view string_view。

*pos*<br/>
此 string_view 比較開始處的索引。

*num*<br/>
從這個 string_view 要比較的字元數目上限。

*num2*<br/>
中的字元數目上限*strv*進行比較。

*offset*<br/>
索引*strv*比較開始處。

*ptr*<br/>
要與此 string_view 進行比較的 C 字串。

### <a name="return-value"></a>傳回值

此 string_view 是否為負數值小於*strv*或是*ptr*，則為零是否大於此 string_view，如果兩個字元序列相等; 或正的數值*strv*或是*ptr*。

### <a name="remarks"></a>備註

`compare`成員函式執行區分大小寫的比較的全部或一部分的每個字元序列。 

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

## <a name="copy"></a>  basic_string_view::copy

最多指定的數目的字元複製從來源 string_view 中的索引位置到目標字元陣列。 我們建議您改用安全的函式[basic_string_view::_Copy_s](#_copy_s)改。

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*ptr*<br/>
要複製元素的目標字元陣列。

*count*<br/>
要複製，最多會從來源 string_view 的字元數。

*offset*<br/>
在其複本的建立來源 string_view 開頭位置。

### <a name="return-value"></a>傳回值

實際複製的字元數。

### <a name="remarks"></a>備註

不會將 Null 字元附加至複本結尾。

## <a name="_copy_s"></a>  basic_string_view::_Copy_s

安全 CRT 複製函式，而不是使用[複製](#copy)。

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>參數

*dest*<br/>
要複製元素的目標字元陣列。

*dest_size*<br/>
大小*dest*。

_*計數*進行複製，最多會從來源字串的字元數。

*_Off*<br/>
來源字串中要建立複本的開始位置。

### <a name="return-value"></a>傳回值

實際複製的字元數。

### <a name="remarks"></a>備註

不會將 Null 字元附加至複本結尾。

 如需詳細資訊，請參閱 < [c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="crbegin"></a>  basic_string_view::crbegin

傳回定址反轉 string_view 中的第一個元素 const_reverse_iterator。

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

Const_reverse_iterator 定址反轉的 string_view 中的第一個元素。 

## <a name="crend"></a>  basic_string_view::crend

與相同[rend](#rend)。 

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>傳回值

傳回定址反轉的 string_view 結尾的其中一個 const_reverse_iterator。

## <a name="data"></a>  basic_string_view::data

傳回 const 字元序列的物件用來建構 string_view 的未經處理的非主控指標。

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>傳回值

指標-至-常數的字元序列的第一個元素。

### <a name="remarks"></a>備註

指標無法修改資料的字元。

一連串的 string_view 字元不一定是以 null 結尾。 傳回型別`data`不是有效的 C 字串，因為不附加任何 null 字元。 Null 字元 '\0' 物件的型別 string_view 中沒有任何特殊意義，並可與任何其他字元一樣 string_view 物件的一部分。

## <a name="empty"></a>  basic_string_view::empty

測試是否 string_view 包含字元。

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>傳回值

**true** string_view 物件不包含任何字元; 如果**false**有至少一個字元。

### <a name="remarks"></a>備註

此成員函式相當於[大小](#size)（) = = 0。

## <a name="end"></a>  basic_string_view::end

傳回隨機存取指向其中最後一個元素的 const_iterator。

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>傳回值

傳回隨機存取指向其中最後一個元素的 const_iterator。

### <a name="remarks"></a>備註

`end` 用來測試是否 const_iterator 已到達其 string_view 的結尾。 `end` 所傳回的值不應該取值。

## <a name="find"></a>  basic_string_view::find

字元或符合指定的一連串字元的子字串的第一個以正向方向搜尋 string_view。

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*str*<br/>
若要搜尋之成員函式的 string_view。

*chVal*<br/>
要搜尋之成員函式的字元值。

*offset*<br/>
若要開始搜尋時的索引。

*ptr*<br/>
若要搜尋之成員函式的 C 字串。

*count*<br/>
中的字元數*ptr*，從第一個字元開始往前計數。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="find_first_not_of"></a>  basic_string_view::find_first_not_of

搜尋不是元素指定的 string_view 或轉換的字串物件的第一個字元。

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*str*<br/>
若要搜尋之成員函式的 string_view。

*chVal*<br/>
要搜尋之成員函式的字元值。

*offset*<br/>
若要開始搜尋時的索引。

*ptr*<br/>
若要搜尋之成員函式的 C 字串。

*count*<br/>
從要搜尋之成員函式的 C 字串中的第一個字元開始往前計數的字元數目。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="find_first_of"></a>  basic_string_view::find_first_of

搜尋符合指定的 string_view 之任何元素的第一個字元。

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>參數

*chVal*<br/>
要搜尋之成員函式的字元值。

*offset*<br/>
若要開始搜尋時的索引。

*ptr*<br/>
若要搜尋之成員函式的 C 字串。

*count*<br/>
從要搜尋之成員函式的 C 字串中的第一個字元開始往前計數的字元數目。

*str*<br/>
若要搜尋之成員函式的 string_view。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `npos`。

## <a name="find_last_not_of"></a>  basic_string_view::find_last_not_of

不是指定 string_view 之任何元素的最後一個字元的搜尋。

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*str*<br/>
若要搜尋之成員函式的 string_view。

*chVal*<br/>
要搜尋之成員函式的字元值。

*offset*<br/>
若要完成搜尋時的索引。

*ptr*<br/>
若要搜尋之成員函式的 C 字串。

*count*<br/>
字元數，在開始往前計數的第一個字元，從*ptr*。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的第一個字元的索引，否則為 `string_view::npos`。

## <a name="find_last_of"></a>  basic_string_view::find_last_of

搜尋符合指定的 string_view 之任何元素的最後一個字元。

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*str*<br/>
若要搜尋之成員函式的 string_view。

*chVal*<br/>
要搜尋之成員函式的字元值。

*offset*<br/>
若要完成搜尋時的索引。

*ptr*<br/>
若要搜尋之成員函式的 C 字串。

*count*<br/>
從要搜尋之成員函式的 C 字串中的第一個字元開始往前計數的字元數目。

### <a name="return-value"></a>傳回值

在成功時，為搜尋的子字串的最後一個字元的索引；否則為 `npos`。

## <a name="front"></a>  basic_string_view::front

Const_reference 回到第一個項目。

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>傳回值

Const_reference 第一個項目。

### <a name="remarks"></a>備註

如果是空的 string_view，則會擲回例外狀況。

## <a name="length"></a> basic_string_view::length

傳回目前的元素數目。

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>備註

此成員函式與 [size](#size) 相同。

## <a name="max_size"></a>  basic_string_view::max_size

傳回 string_view 可包含的字元的數上限。

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>傳回值

String_view 可以包含的字元數目上限。

### <a name="remarks"></a>備註

類型的例外狀況[length_error](../standard-library/length-error-class.md)就會擲回一項作業會產生長度大於 string_view `max_size()`。

## <a name="op_eq"></a>  basic_string_view::operator=

給另一個 string_view string_view 或轉換的字串物件。

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```
### <a name="example"></a>範例

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```
## <a name="op_at"></a>  basic_string_view::operator[]

提供的字元 const_reference 具有指定之索引。

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>參數

*offset*<br/>
要參考之項目的索引。

### <a name="return-value"></a>傳回值

Const_reference 至指定的參數索引位置處的字元。

### <a name="remarks"></a>備註

第一個元素的索引為零，而且下列項目編製索引連續的正數的整數，以便長度的 string_view *n*已*n*數個項目編製索引*n* -1。

`operator[]` 速度比成員函式[在](#at)提供 string_view 的項目 「 讀取 」 權限。

`operator[]` 不會檢查做為引數傳遞的索引是否有效。 無效的索引傳遞至`operator[]`導致未定義的行為。

如果基礎字串資料被修改或刪除擁有的物件，傳回的參考可能會失效。

進行編譯時[\_迭代器\_偵錯\_層級](../standard-library/iterator-debug-level.md)設為 1 或 2，則執行階段會發生錯誤如果您嘗試存取的 string_view 界限以外的項目。 如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md)。

## <a name="rbegin"></a>  basic_string_view::rbegin

傳回在反轉 string_view 的第一個元素的 const 迭代器。

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>傳回值

傳回在反轉的 string_view，定址在對應的未反轉 string_view 的最後一個元素的第一個元素的隨機存取迭代器。

### <a name="remarks"></a>備註

`rbegin` 用於反轉 string_view 就如同[開始](#begin)string_view 搭配使用。 `rbegin` 可用來向後初始化反覆項目。

## <a name="remove_prefix"></a> basic_string_view::remove_prefix

將指標向前移所指定的元素數目。

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>備註

會保留不變的基礎資料。 將 string_view 指標向前移的 n 個項目和設定私用`size`大小-n 的資料成員。

## <a name="remove_suffix"></a> basic_string_view::remove_suffix

檢視的大小減少為指定數目的項目從 [上一步]。

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>備註

它不會變更，會保留基礎資料和指標。 設定私用`size`大小-n 的資料成員。

## <a name="rend"></a>  basic_string_view::rend

傳回常數迭代器，指向一個反向的 string_view 中最後一個元素。

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>傳回值

Const 反轉隨機存取迭代器，指向一個反向的 string_view 中最後一個元素。

### <a name="remarks"></a>備註

`rend` 用於反轉 string_view 就如同[結束](#end)string_view 搭配使用。 `rend` 可用來測試是否的反向迭代器已到達其 string_view 的結尾。 `rend` 所傳回的值不應該取值。

## <a name="rfind"></a>  basic_string_view::rfind

搜尋符合指定的字元序列的子字串的反向 string_view。

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>參數

*chVal*<br/>
要搜尋之成員函式的字元值。

*offset*<br/>
若要開始搜尋時的索引。

*ptr*<br/>
若要搜尋之成員函式的 C 字串。

*count*<br/>
從要搜尋之成員函式的 C 字串中的第一個字元開始往前計數的字元數目。

*str*<br/>
若要搜尋之成員函式的 string_view。

### <a name="return-value"></a>傳回值

當成功; 的子字串的第一個字元的索引否則`npos`。

## <a name="size"></a>  basic_string_view::size

String_view 中傳回的項目數。

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>傳回值

String_view 的長度。

### <a name="remarks"></a>備註

String_view 可以修改它的長度，例如`remove_prefix`和`remove_suffix`。 這不會修改基礎字串資料，因為 string_view 的大小不一定是基礎資料的大小。

## <a name="substr"></a>  basic_string_view::substr

傳回表示從指定之位置的指定的字元數 （最多） string_view。

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>參數

*offset*<br/>
尋找從中建立複本，預設值為 0 的位置處的項目索引。

*count*<br/>
要納入的子字串，如果它們存在的字元數。

### <a name="return-value"></a>傳回值

String_view 物件，表示指定的子序列的項目。

## <a name="swap"></a>  basic_string_view::swap

交換兩個 string_views，亦即基礎字串資料和指標的大小值。

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>參數

*sv*<br/>
其指標和大小值都要交換的目的地 string_view 來源 string_view。

## <a name="see-also"></a>另請參閱

[\<string_view>](../standard-library/string-view.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
