---
title: path 類別 | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::path
dev_langs:
- C++
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7674f07c92f8a0c9d8a9070f3f99e00dfde39140
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235460"
---
# <a name="path-class"></a>path 類別

**路徑**類別會儲存類型的物件`string_type`，稱為`myname`這裡基於的說明，適合用為路徑名稱。 `string_type` 是的同義字`basic_string<value_type>`，其中`value_type`同義**wchar_t**上 Windows 或**char** POSIX 上。

如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class path;
```

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[path](#path)|建構 `path`。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[const_iterator](#const_iterator)|`iterator` 的同義字。|
|[iterator](#iterator)|雙向常數迭代器，指定`path`元件`myname`。|
|[string_type](#string_type)|此類型是 `basic_string<value_type>` 的同義字。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[append](#append)|將指定的順序，以附加`mypath`、 轉換和視需要插入 preferred_separator。|
|[assign](#assign)|取代`mypath`以指定的序列，視需要轉換。|
|[begin](#begin)|傳回`path::iterator`指定的路徑名稱中的第一個路徑元素，如果有的話。|
|[c_str](#c_str)|傳回的第一個字元的指標`mypath`。|
|[clear](#clear)|執行`mypath.clear()`。|
|[compare](#compare)|傳回比較值。|
|[concat](#compare)|將指定的順序，以附加`mypath`、 轉換 （但不是插入分隔符號） 所需。|
|[empty](#empty)|傳回 `mypath.empty()`。|
|[end](#end)|傳回結束序列迭代器的型別`iterator`。|
|[延伸模組](#extension)|傳回的尾碼`filename()`。|
|[filename](#filename)|傳回 myname 的根目錄元件，即 `empty() path() : *--end()`。 元件可能是空的。|
|[path::string、wstring、u8string、u16string、generic_string](#generic_string)|傳回 `this->string<Elem, Traits, Alloc>(al)` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。|
|[generic_u16string](#generic_u16string)|傳回 `u16string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。|
|[generic_u32string](#generic_u32string)|傳回 `u32string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。|
|[generic_u8string](#generic_u8string)|傳回 `u8string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。|
|[generic_wstring](#generic_wstring)|傳回 `wstring()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。|
|[has_extension](#has_extension)|傳回 `!extension().empty()`。|
|[has_filename](#has_filename)|傳回 `!filename().empty()`。|
|[has_parent_path](#has_parent_path)|傳回 `!parent_path().empty()`。|
|[has_relative_path](#has_relative_path)|傳回 `!relative_path().empty()`。|
|[has_root_directory](#has_root_directory)|傳回 `!root_directory().empty()`。|
|[has_root_name](#has_root_name)|傳回 `!root_name().empty()`。|
|[has_root_path](#has_root_path)|傳回 `!root_path().empty()`。|
|[has_stem](#has_stem)|傳回 `!stem().empty()`。|
|[is_absolute](#is_absolute)|針對 Windows，則函數會傳回`has_root_name() && has_root_directory()`。 至於 Posix，函式會傳回`has_root_directory()`。|
|[is_relative](#is_relative)|傳回 `!is_absolute()`。|
|[make_preferred](#make_preferred)|視需要請將每個分隔符號轉換成 preferred_separator 」。|
|[Native.Xyz](#native)|傳回 `myname`。|
|[parent_path](#parent_path)|傳回父路徑元件`myname`。|
|[preferred_separator](#preferred_separator)|常數物件會提供慣用的字元分隔路徑元件，隨主機作業系統而異。 |
|[relative_path](#relative_path)|傳回的相對路徑元件`myname`。 |
|[remove_filename](#remove_filename)|移除檔案名稱。|
|[replace_extension](#replace_extension)|取代的延伸`myname`。 |
|[replace_filename](#replace_filename)|RReplaces 檔案名稱。|
|[root_directory](#root_directory)|傳回的根目錄元件`myname`。 |
|[root_name&lt](#root_name)|傳回的根名稱元件`myname`。 |
|[root_path](#root_path)|傳回的根路徑元件`myname`。|
|[stem](#stem)|傳回`stem`元件`myname`。|
|[string](#string)|儲存中的序列轉換`mypath`。|
|[swap](#swap)|執行`swap(mypath, right.mypath)`。|
|[u16string](#u16string)|儲存中的序列轉換`mypath`utf-16，然後傳回類型的物件中所儲存`u16string`。|
|[u32string](#u32string)|儲存中的序列轉換`mypath`UTF-32，然後傳回類型的物件中所儲存`u32string`。|
|[u8string](#u8string)|儲存中的序列轉換`mypath`utf-8，然後傳回類型的物件中所儲存`u8string`。|
|[value_type](#value_type)|此類型描述主機作業系統偏好的路徑元素。|
|[wstring](#wstring)|儲存中的序列轉換`mypath`成主機系統偏好的編碼`wchar_t`順序和類型的物件中所儲存的傳回`wstring`。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_as)|路徑的項目取代為另一個路徑的複本。|
|[operator+=](#op_add)|各種`concat`運算式。|
|[operator/=](#op_divide)|各種`append`運算式。|
|[string_type 運算子](#op_string)|傳回 `myname`。|

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：** std::experimental::filesystem

## <a name="append"></a> path:: append

將指定的順序，以附加`mypath`、 轉換和插入`preferred_separator`視。

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*source*<br/>
指定的順序。

*first*<br/>
指定序列的開頭。

*最後一個*<br/>
指定序列的結尾。

## <a name="assign"></a> path:: assign

取代`mypath`以指定的序列，視需要轉換。

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*source*<br/>
指定的順序。

*first*<br/>
指定序列的開頭。

*最後一個*<br/>
指定序列的結尾。

## <a name="begin"></a> path:: begin

傳回`path::iterator`指定的路徑名稱中的第一個路徑元素，如果有的話。

```cpp
iterator begin() const;
```

## <a name="c_str"></a> path::c_str

傳回的第一個字元的指標`mypath`。

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a> path:: clear

執行`mypath.clear()`。

```cpp
void clear() noexcept;
```

## <a name="compare"></a> path:: compare

第一個函式會傳回 `mypath.compare(pval.native())`。 第二個函式會傳回 `mypath.compare(str)`。 第三個函式會傳回`mypath.compare(ptr)`。

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>參數

*pval*<br/>
要比較的路徑。

*str*<br/>
要比較的字串。

*ptr*<br/>
要比較的指標。

## <a name="concat"></a> path:: concat

將指定的順序，以附加`mypath`、 轉換 （但不是插入分隔符號） 所需。

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*source*<br/>
指定的順序。

*first*<br/>
指定序列的開頭。

*最後一個*<br/>
指定序列的結尾。

## <a name="const_iterator"></a> path::const_iterator

`iterator` 的同義字。

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a> path:: empty

傳回 `mypath.empty()`。

```cpp
bool empty() const noexcept;
```

## <a name="end"></a> path:: end

傳回結束序列迭代器的型別`iterator`。

```cpp
iterator end() const;
```

## <a name="extension"></a> path:: extension

傳回的尾碼`filename()`。

```cpp
path extension() const;
```

### <a name="remarks"></a>備註

傳回的尾碼`filename() X`以便：

如果`X == path(".") || X == path("..")`或者`X`沒有點後, 置詞是空的。

否則後置詞開頭 (並包含) 會是最右邊的點。

## <a name="filename"></a> path:: filename

傳回 myname 的根目錄元件，即 `empty() path() : *--end()`。 元件可能是空的。

```cpp
path filename() const;
```

## <a name="generic_string"></a> path::generic_string

傳回 `this->string<Elem, Traits, Alloc>(al)` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a> path::generic_u16string

傳回 `u16string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a> path::generic_u32string

傳回 `u32string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a> path::generic_u8string

傳回 `u8string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a> path::generic_wstring

傳回 `wstring()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a> path::has_extension

傳回 `!extension().empty()`。

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a> path:: has_filename

傳回 `!filename().empty()`。

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a> path:: has_parent_path

傳回 `!parent_path().empty()`。

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a> path:: has_relative_path

傳回 `!relative_path().empty()`。

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a> path:: has_root_directory

傳回 `!root_directory().empty()`。

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a> path:: has_root_name

傳回 `!root_name().empty()`。

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a> path:: has_root_path

傳回 `!root_path().empty()`。

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a> path::has_stem

傳回 `!stem().empty()`。

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a> path:: is_absolute

針對 Windows，則函數會傳回`has_root_name() && has_root_directory()`。 至於 Posix，函式會傳回`has_root_directory()`。

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a> path:: is_relative

傳回 `!is_absolute()`。

```cpp
bool is_relative() const;
```

## <a name="iterator"></a> path:: iterator

雙向常數迭代器，以指定的路徑元件`myname`。

```cpp
class iterator
   {
   // bidirectional iterator for path
   typedef bidirectional_iterator_tag iterator_category;
   typedef path_type value_type;
   typedef ptrdiff_t difference_type;
   typedef const value_type *pointer;
   typedef const value_type& reference;
   // ...
   };
```

### <a name="remarks"></a>備註

此類別會描述雙向常數迭代器，指定`path`元件`myname`序列中：

1. 根名稱，如果有的話

1. 根目錄，如果有的話

1. 其餘目錄項目之父代`path`，如果有的話，結尾的檔案名稱，如果有的話

針對`pval`型別的物件`path`:

1. `path::iterator X = pval.begin()` 指定第一個`path`項目中的路徑名稱，如果有的話。

1. `X == pval.end()` 時為 true`X`剛好超過序列結尾的點的元件。

3. `*X` 傳回符合目前元件的字串

1. 如果有的話，`++X` 會指定順序中的下一個元件。

1. 如果有的話，`--X` 會指定順序中的上一個元件。

1. 改變`myname`失效的指定項目中的所有迭代器`myname`。

## <a name="make_preferred"></a> path:: make_preferred

將轉換至每個分隔符號`preferred_separator`視。

```cpp
path& make_preferred();
```

## <a name="native"></a> path::native

傳回 `myname`。

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a> path:: operator =

路徑的項目取代為另一個路徑的複本。

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>參數

*right*<br/>
[路徑](../standard-library/path-class.md)複製到`path`。

*source*<br/>
來源路徑。

### <a name="remarks"></a>備註

第一個成員運算子複製`right.myname`至`myname`。 第二個成員運算子將`right.myname`至`myname`。 第三個成員運算子的行為相同`*this = path(source)`。

## <a name="op_add"></a> path:: operator + =

各種`concat`運算式。

```cpp
path& operator+=(const path& right);
path& operator+=(const string_type& str);
path& operator+=(const value_type *ptr);
path& operator+=(value_type elem);

template <class Source>
path& operator+=(const Source& source);

template <class Elem>
path& operator+=(Elem elem);
```

### <a name="parameters"></a>參數

*right*<br/>
加入的路徑。

*str*<br/>
已新增的字串。

*ptr*<br/>
已新增的指標。

*Elem*<br/>
已加入`value_type`或`Elem`。

*source*<br/>
已新增的來源。

### <a name="remarks"></a>備註

成員函式的行為與下列對應的運算式相同：

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="op_divide"></a> path:: operator / =

各種`append`運算式。

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>參數

*right*<br/>
加入的路徑。

*source*<br/>
已新增的來源。

### <a name="remarks"></a>備註

成員函式的行為與下列對應的運算式相同：

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a> path:: operator string_type

傳回 `myname`。

```cpp
operator string_type() const;
```

## <a name="parent_path"></a> path:: parent_path

傳回父路徑元件`myname`。

```cpp
path parent_path() const;
```

### <a name="remarks"></a>備註

傳回父路徑元件`myname`，特別的前置詞`myname`移除之後`filename().native()`和任何正前面的目錄分隔符號。 (同樣地，如果`begin() != end()`，它是在範圍內的所有元素的組合`[begin(), --end())`連續套用`operator/=`。)元件可能是空的。

## <a name="path"></a> path:: path

建構`path`以各種方式。

```cpp
path();

path(const path& right);
path(path&& right) noexcept;

template <class Source>
path(const Source& source);

template <class Source>
path(const Source& source, const locale& loc);

template <class InIt>
path(InIt first, InIt last);

template <class InIt>
path(InIt first, InIt last, const locale& loc);
```

### <a name="parameters"></a>參數

*right*<br/>
要從中複製建構的路徑的路徑。

*source*<br/>
要從中複製建構的路徑的來源。

*當地語系化*<br/>
指定的地區設定。

*first*<br/>
要複製之第一個元素的位置。

*最後一個*<br/>
要複製的最後一個元素的位置。

### <a name="remarks"></a>備註

所有建構的建構函式`myname`以各種方式：

針對`path()`很`myname()`。

針對`path(const path& right`) 是`myname(right.myname)`。

針對`path(path&& right)`很`myname(right.myname)`。

針對`template<class Source> path(const Source& source)`很`myname(source)`。

針對`template<class Source> path(const Source& source, const locale& loc)`很`myname(source)`，取得任何需要的 codecvt facet 從`loc`。

針對`template<class InIt> path(InIt first, InIt last)`很`myname(first, last)`。

針對`template<class InIt> path(InIt first, InIt last, const locale& loc)`很`myname(first, last)`，取得任何需要的 codecvt facet 從`loc`。

## <a name="preferred_separator"></a> path::preferred_separator

常數物件會提供慣用的字元分隔路徑元件，隨主機作業系統而異。

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>備註

請注意，Windows 大部分的內容同樣允許在這個位置使用 L'/'。

## <a name="relative_path"></a> path:: relative_path

傳回的相對路徑元件`myname`。

```cpp
path relative_path() const;
```

### <a name="remarks"></a>備註

傳回的相對路徑元件`myname`，特別是尾碼`myname`移除之後`root_path().native()`和任何緊鄰的備援目錄分隔符號。 元件可能是空的。

## <a name="remove_filename"></a> path:: remove_filename

移除檔案名稱。

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a> path:: replace_extension

取代的延伸`myname`。

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>參數

*newext*<br/>
新的延伸模組。

### <a name="remarks"></a>備註

首先會移除後置詞`extension().native()`從`myname`。 然後，如果`!newext.empty() && newext[0] != dot`(其中`dot`是`*path(".").c_str()`)，然後`dot`附加至`myname`。 然後*newext*附加至`myname`。

## <a name="replace_filename"></a> path:: replace_filename

取代檔案名稱。

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>參數

*pval*<br/>
檔名的路徑。

### <a name="remarks"></a>備註

成員函式會執行：

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a> path:: root_directory

傳回的根目錄元件`myname`。

```cpp
path root_directory() const;
```

### <a name="remarks"></a>備註

元件可能是空的。

## <a name="root_name"></a> path:: root_name

傳回的根名稱元件`myname`。

```cpp
path root_name() const;
```

### <a name="remarks"></a>備註

元件可能是空的。

## <a name="root_path"></a> path:: root_path

傳回的根路徑元件`myname`。

```cpp
path root_path() const;
```

### <a name="remarks"></a>備註

傳回的根路徑元件`myname`，具體來說`root_name()`  /  `root_directory`。 元件可能是空的。

## <a name="stem"></a> path:: stem

傳回`stem`元件`myname`。

```cpp
path stem() const;
```

### <a name="remarks"></a>備註

傳回`stem`元件`myname`，特別`filename().native()`使用任何後置`extension().native()`移除。 元件可能是空的。

## <a name="string"></a> path:: string

儲存中的序列轉換`mypath`。

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>備註

儲存在序列的第一個 （範本） 的成員函式轉換`mypath`一樣：

1. `string()` 的 `string<char, Traits, Alloc>()`

1. `wstring()` 的 `string<wchar_t, Traits, Alloc>()`

1. `u16string()` 的 `string<char16_t, Traits, Alloc>()`

1. `u32string()` 的 `string<char32_t, Traits, Alloc>()`

儲存在序列的第二個成員函式轉換`mypath`成主機系統偏好的編碼**char**序列，並傳回它的類型物件中所儲存`string`。

## <a name="string_type"></a> path::string_type

此類型是 `basic_string<value_type>` 的同義字。

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a> path:: swap

執行`swap(mypath, right.mypath)`。

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a> path::u16string

儲存中的序列轉換`mypath`utf-16，然後傳回類型的物件中所儲存`u16string`。

```cpp
u16string u16string() const;
```

## <a name="u32string"></a> path::u32string

儲存中的序列轉換`mypath`UTF-32，然後傳回類型的物件中所儲存`u32string`。

```cpp
u32string u32string() const;
```

## <a name="u8string"></a> path::u8string

儲存中的序列轉換`mypath`utf-8，然後傳回類型的物件中所儲存`u8string`。

```cpp
string u8string() const;
```

## <a name="value_type"></a> path::value_type

此類型描述`path`主機作業系統偏好的項目。

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a> path::wstring

儲存中的序列轉換`mypath`成主機系統偏好的編碼**wchar_t**序列，並傳回它的類型物件中所儲存`wstring`。

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
