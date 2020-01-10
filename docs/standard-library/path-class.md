---
title: path 類別
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 0bc26bb04464c52ed08d46e6a12c12cae6909d6f
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898801"
---
# <a name="path-class"></a>path 類別

**Path**類別會儲存型別為 `string_type`的物件，在這裡稱為「`myname`」（展示），適合當做路徑名稱使用。 `string_type` 是 `basic_string<value_type>`的同義字，其中 `value_type` 是在 Windows 上**wchar_t**的同義字，或 POSIX 上的**char** 。

如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class path;
```

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[path](#path)|建構 `path`。|

### <a name="typedefs"></a>Typedef

|類型名稱|描述|
|-|-|
|[const_iterator](#const_iterator)|`iterator` 的同義字。|
|[iterator](#iterator)|指定 `myname`之 `path` 元件的雙向常數反覆運算器。|
|[string_type](#string_type)|此類型是 `basic_string<value_type>`的同義字。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[append](#append)|將指定的序列附加至 `mypath`，並視需要轉換和插入 preferred_separator。|
|[assign](#assign)|以指定的序列取代 `mypath`，並視需要進行轉換。|
|[begin](#begin)|傳回 `path::iterator`，指定路徑名稱中的第一個路徑元素（如果有的話）。|
|[c_str](#c_str)|傳回 `mypath`中第一個字元的指標。|
|[clear](#clear)|執行 `mypath.clear()`。|
|[compare](#compare)|傳回比較值。|
|[concat](#compare)|將指定的序列附加至 `mypath`，並視需要轉換（但不插入分隔符號）。|
|[empty](#empty)|傳回 `mypath.empty()`。|
|[end](#end)|傳回 `iterator`類型的序列結尾反覆運算器。|
|[號](#extension)|傳回 `filename()`的尾碼。|
|[filename](#filename)|傳回 myname 的根目錄元件，即 `empty() path() : *--end()`。 元件可能是空的。|
|[generic_string](#generic_string)|傳回 `this->string<Elem, Traits, Alloc>(al)` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。|
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
|[is_absolute](#is_absolute)|若為 Windows，此函式會傳回 `has_root_name() && has_root_directory()`。 若為 POSIX，函數會傳回 `has_root_directory()`。|
|[is_relative](#is_relative)|傳回 `!is_absolute()`。|
|[make_preferred](#make_preferred)|視需要將每個分隔符號轉換成 preferred_separator。|
|[Native.Xyz](#native)|傳回 `myname`。|
|[parent_path](#parent_path)|傳回 `myname`的父路徑元件。|
|[preferred_separator](#preferred_separator)|常數物件會提供慣用的字元分隔路徑元件，隨主機作業系統而異。 |
|[relative_path](#relative_path)|傳回 `myname`的相對路徑元件。 |
|[remove_filename](#remove_filename)|移除檔案名。|
|[replace_extension](#replace_extension)|取代 `myname`的延伸模組。 |
|[replace_filename](#replace_filename)|RReplaces 檔案名。|
|[root_directory](#root_directory)|傳回 `myname`的根目錄元件。 |
|[root_name](#root_name)|傳回 `myname`的根名稱元件。 |
|[root_path](#root_path)|傳回 `myname`的根路徑元件。|
|[致](#stem)|傳回 `myname`的 `stem` 元件。|
|[string](#string)|轉換儲存在 `mypath`中的序列。|
|[swap](#swap)|執行 `swap(mypath, right.mypath)`。|
|[u16string](#u16string)|將儲存在 `mypath` 中的序列轉換成 UTF-16，並傳回它儲存在 `u16string`類型的物件中。|
|[u32string](#u32string)|將儲存在 `mypath` 中的序列轉換成 UTF-32，並傳回儲存在 `u32string`類型物件中的。|
|[u8string](#u8string)|將儲存在 `mypath` 中的序列轉換成 UTF-8，並傳回它儲存在 `u8string`類型的物件中。|
|[value_type](#value_type)|此類型描述主機作業系統偏好的路徑元素。|
|[wstring](#wstring)|將儲存在 `mypath` 中的序列轉換成主機系統針對 `wchar_t` 序列所採用的編碼，並傳回它儲存在 `wstring`類型物件中。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_as)|以另一個路徑的複本取代路徑的元素。|
|[operator+=](#op_add)|各種 `concat` 運算式。|
|[operator/=](#op_divide)|各種 `append` 運算式。|
|[運算子 string_type](#op_string)|傳回 `myname`。|

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：** std::experimental::filesystem

## <a name="append"></a>path：： append

將指定的序列附加至 `mypath`，並視需要轉換和插入 `preferred_separator`。

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*來源*\
指定的順序。

*第一個*\
開始指定的順序。

*上次*\
指定序列的結尾。

## <a name="assign"></a>path：： assign

以指定的序列取代 `mypath`，並視需要進行轉換。

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*來源*\
指定的順序。

*第一個*\
開始指定的順序。

*上次*\
指定序列的結尾。

## <a name="begin"></a>path：： begin

傳回 `path::iterator`，指定路徑名稱中的第一個路徑元素（如果有的話）。

```cpp
iterator begin() const;
```

## <a name="c_str"></a>path：： c_str

傳回 `mypath`中第一個字元的指標。

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a>path：： clear

執行 `mypath.clear()`。

```cpp
void clear() noexcept;
```

## <a name="compare"></a>path：： compare

第一個函式會傳回 `mypath.compare(pval.native())`。 第二個函式會傳回 `mypath.compare(str)`。 第三個函式會傳回 `mypath.compare(ptr)`。

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>參數

*pval*\
要比較的路徑。

*str*\
要比較的字串。

*ptr*\
要比較的指標。

## <a name="concat"></a>path：： concat

將指定的序列附加至 `mypath`，並視需要轉換（但不插入分隔符號）。

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*來源*\
指定的順序。

*第一個*\
開始指定的順序。

*上次*\
指定序列的結尾。

## <a name="const_iterator"></a>path：： const_iterator

`iterator` 的同義字。

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>path：： empty

傳回 `mypath.empty()`。

```cpp
bool empty() const noexcept;
```

## <a name="end"></a>path：： end

傳回 `iterator`類型的序列結尾反覆運算器。

```cpp
iterator end() const;
```

## <a name="extension"></a>path：： extension

傳回 `filename()`的尾碼。

```cpp
path extension() const;
```

### <a name="remarks"></a>備註

傳回 `filename() X` 的尾碼，如下所示：

如果 `X == path(".") || X == path("..")` 或 `X` 不包含任何點，則尾碼會是空的。

否則後置詞開頭 (並包含) 會是最右邊的點。

## <a name="filename"></a>path：： filename

傳回 myname 的根目錄元件，即 `empty() path() : *--end()`。 元件可能是空的。

```cpp
path filename() const;
```

## <a name="generic_string"></a>path：： generic_string

傳回 `this->string<Elem, Traits, Alloc>(al)` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a>path：： generic_u16string

傳回 `u16string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a>path：： generic_u32string

傳回 `u32string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a>path：： generic_u8string

傳回 `u8string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a>path：： generic_wstring

傳回 `wstring()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a>path：： has_extension

傳回 `!extension().empty()`。

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a>path：： has_filename

傳回 `!filename().empty()`。

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a>path：： has_parent_path

傳回 `!parent_path().empty()`。

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a>path：： has_relative_path

傳回 `!relative_path().empty()`。

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a>path：： has_root_directory

傳回 `!root_directory().empty()`。

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>path：： has_root_name

傳回 `!root_name().empty()`。

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a>path：： has_root_path

傳回 `!root_path().empty()`。

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>path：： has_stem

傳回 `!stem().empty()`。

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>path：： is_absolute

若為 Windows，此函式會傳回 `has_root_name() && has_root_directory()`。 若為 POSIX，函數會傳回 `has_root_directory()`。

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>path：： is_relative

傳回 `!is_absolute()`。

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>path：： iterator

雙向常數反覆運算器，指定 `myname`的路徑元件。

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

類別描述雙向常數反覆運算器，指定序列中 `myname` 的 `path` 元件：

1. 根名稱，如果有的話

1. 根目錄，如果有的話

1. 父 `path`的其餘目錄元素（如果有的話），以檔案名結尾（如果有的話）

針對 `pval` `path`類型的物件：

1. `path::iterator X = pval.begin()` 指定路徑名稱中的第一個 `path` 元素（如果有的話）。

1. 當 `X` 點剛好超過元件序列的結尾時，`X == pval.end()` 為 true。

3. `*X` 傳回符合目前元件的字串

1. 如果有的話，`++X` 會指定順序中的下一個元件。

1. 如果有的話，`--X` 會指定順序中的上一個元件。

1. 改變 `myname` 會使在 `myname`中指定元素的所有反覆運算器失效。

## <a name="make_preferred"></a>path：： make_preferred

視需要將每個分隔符號轉換成 `preferred_separator`。

```cpp
path& make_preferred();
```

## <a name="native"></a>path：： native

傳回 `myname`。

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a>path：： operator =

以另一個路徑的複本取代路徑的元素。

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>參數

*right*\
要複製到`path`中的[路徑](../standard-library/path-class.md)。

*來源*\
來源路徑。

### <a name="remarks"></a>備註

第一個成員運算子會將 `right.myname` 複製到 `myname`。 第二個成員運算子會將 `right.myname` 移至 `myname`。 第三個成員運算子的行為與 `*this = path(source)`相同。

## <a name="op_add"></a>path：： operator + =

各種 `concat` 運算式。

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

*right*\
新增的路徑。

*str*\
新增的字串。

*ptr*\
新增的指標。

*elem*\
新增的 `value_type` 或 `Elem`。

*來源*\
新增的來源。

### <a name="remarks"></a>備註

成員函式的行為與下列對應的運算式相同：

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="op_divide"></a>path：： operator/=

各種 `append` 運算式。

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>參數

*right*\
新增的路徑。

*來源*\
新增的來源。

### <a name="remarks"></a>備註

成員函式的行為與下列對應的運算式相同：

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a>path：： operator string_type

傳回 `myname`。

```cpp
operator string_type() const;
```

## <a name="parent_path"></a>路徑：:p arent_path

傳回 `myname`的父路徑元件。

```cpp
path parent_path() const;
```

### <a name="remarks"></a>備註

傳回 `myname`的父路徑元件，特別是移除 `filename().native()` 和任何緊接在前面的目錄分隔符號之後 `myname` 的前置詞。 （同樣地，如果 `begin() != end()`，則會藉由連續套用 `operator/=`，將範圍中的所有元素結合 `[begin(), --end())`。）元件可能是空的。

## <a name="path"></a>路徑：:p 路徑 a)

以各種方式來構造 `path`。

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

*right*\
結構的路徑，即為複本。

*來源*\
結構化路徑是複本的來源。

*loc*\
指定的地區設定。

*第一個*\
要複製之第一個元素的位置。

*上次*\
要複製之最後一個元素的位置。

### <a name="remarks"></a>備註

所有的函式都會以各種方式來 `myname` 構造：

若是 `path()` 則 `myname()`。

若為 `path(const path& right`） `myname(right.myname)`。

若是 `path(path&& right)` 則 `myname(right.myname)`。

若是 `template<class Source> path(const Source& source)` 則 `myname(source)`。

針對 `template<class Source> path(const Source& source, const locale& loc)` `myname(source)`，從 `loc`取得所需的 codecvt facet。

若是 `template<class InIt> path(InIt first, InIt last)` 則 `myname(first, last)`。

針對 `template<class InIt> path(InIt first, InIt last, const locale& loc)` `myname(first, last)`，從 `loc`取得所需的 codecvt facet。

## <a name="preferred_separator"></a>路徑：:p referred_separator

常數物件會提供慣用的字元分隔路徑元件，隨主機作業系統而異。

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>備註

請注意，Windows 大部分的內容同樣允許在這個位置使用 L'/'。

## <a name="relative_path"></a>path：： relative_path

傳回 `myname`的相對路徑元件。

```cpp
path relative_path() const;
```

### <a name="remarks"></a>備註

傳回 `myname`的相對路徑元件，特別是移除 `root_path().native()` 和任何立即後續的重複目錄分隔符號之後，`myname` 的尾碼。 元件可能是空的。

## <a name="remove_filename"></a>path：： remove_filename

移除檔案名。

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a>path：： replace_extension

取代 `myname`的延伸模組。

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>參數

*newext*\
新的延伸模組。

### <a name="remarks"></a>備註

先從 `myname`移除尾碼 `extension().native()`。 然後，如果 `!newext.empty() && newext[0] != dot` （其中 `dot` 為 `*path(".").c_str()`），則 `dot` 會附加至 `myname`。 然後， *newext*會附加至 `myname`。

## <a name="replace_filename"></a>path：： replace_filename

取代 filename。

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>參數

*pval*\
檔案名的路徑。

### <a name="remarks"></a>備註

成員函式會執行：

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a>path：： root_directory

傳回 `myname`的根目錄元件。

```cpp
path root_directory() const;
```

### <a name="remarks"></a>備註

元件可能是空的。

## <a name="root_name"></a>path：： root_name

傳回 `myname`的根名稱元件。

```cpp
path root_name() const;
```

### <a name="remarks"></a>備註

元件可能是空的。

## <a name="root_path"></a>path：： root_path

傳回 `myname`的根路徑元件。

```cpp
path root_path() const;
```

### <a name="remarks"></a>備註

傳回 `myname`的根路徑元件，特別是 `root_name()` / `root_directory`。 元件可能是空的。

## <a name="stem"></a>path：：詞幹

傳回 `myname`的 `stem` 元件。

```cpp
path stem() const;
```

### <a name="remarks"></a>備註

傳回 `myname`的 `stem` 元件，特別是 `filename().native()` 移除的任何尾端 `extension().native()`。 元件可能是空的。

## <a name="string"></a>path：： string

轉換儲存在 `mypath`中的序列。

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>備註

第一個（範本）成員函式會以下列方式轉換儲存在 `mypath` 中的序列：

1. `string()` 代表 `string<char, Traits, Alloc>()`

1. `wstring()` 代表 `string<wchar_t, Traits, Alloc>()`

1. `u16string()` 代表 `string<char16_t, Traits, Alloc>()`

1. `u32string()` 代表 `string<char32_t, Traits, Alloc>()`

第二個成員函式會將儲存在 `mypath` 中的序列轉換成**char**序列的主機系統所採用的編碼，並將它儲存在 `string`類型的物件中。

## <a name="string_type"></a>path：： string_type

此類型是 `basic_string<value_type>`的同義字。

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a>path：： swap

執行 `swap(mypath, right.mypath)`。

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a>path：： u16string

將儲存在 `mypath` 中的序列轉換成 UTF-16，並傳回它儲存在 `u16string`類型的物件中。

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>path：： u32string

將儲存在 `mypath` 中的序列轉換成 UTF-32，並傳回儲存在 `u32string`類型物件中的。

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>path：： u8string

將儲存在 `mypath` 中的序列轉換成 UTF-8，並傳回它儲存在 `u8string`類型的物件中。

```cpp
string u8string() const;
```

## <a name="value_type"></a>path：： value_type

此類型描述主機作業系統所優先的 `path` 元素。

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a>path：： wstring

將儲存在 `mypath` 中的序列轉換成主機系統針對**wchar_t**序列所採用的編碼，並傳回它儲存在 `wstring`類型物件中。

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
