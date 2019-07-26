---
title: path 類別
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 10c865aa2bc2431850c69e9dfedbef37414b2cb9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455104"
---
# <a name="path-class"></a>path 類別

**Path**類別會儲存類型`string_type`的物件, `myname`在這裡是為了展示的目的, 適合當做路徑名稱使用。 `string_type``basic_string<value_type>`是的同義字, `value_type`其中是 Windows 上的**wchar_t**同義字或 POSIX 上的**char** 。

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
|[iterator](#iterator)|雙向常數反覆運算器, 指定`path`的`myname`元件。|
|[string_type](#string_type)|此類型是 `basic_string<value_type>` 的同義字。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[append](#append)|將指定的序列附加`mypath`至, 並視需要轉換和插入 preferred_separator。|
|[assign](#assign)|取代`mypath`為指定的序列, 視需要進行轉換。|
|[begin](#begin)|傳回, `path::iterator`指定路徑名稱中的第一個路徑元素 (如果有的話)。|
|[c_str](#c_str)|傳回中`mypath`第一個字元的指標。|
|[clear](#clear)|執行`mypath.clear()`。|
|[compare](#compare)|傳回比較值。|
|[concat](#compare)|視需要將指定的`mypath`序列附加至、轉換 (但不插入分隔符號)。|
|[empty](#empty)|傳回 `mypath.empty()`。|
|[end](#end)|傳回類型`iterator`的結束序列反覆運算器。|
|[號](#extension)|傳回的尾碼`filename()`。|
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
|[is_absolute](#is_absolute)|若為 Windows, 此`has_root_name() && has_root_directory()`函式會傳回。 若為 Posix, `has_root_directory()`函式會傳回。|
|[is_relative](#is_relative)|傳回 `!is_absolute()`。|
|[make_preferred](#make_preferred)|視需要將每個分隔符號轉換成 preferred_separator。|
|[Native.Xyz](#native)|傳回 `myname`。|
|[parent_path](#parent_path)|傳回的`myname`父路徑元件。|
|[preferred_separator](#preferred_separator)|常數物件會提供慣用的字元分隔路徑元件，隨主機作業系統而異。 |
|[relative_path](#relative_path)|傳回的`myname`相對路徑元件。 |
|[remove_filename](#remove_filename)|移除檔案名。|
|[replace_extension](#replace_extension)|取代的延伸`myname`模組。 |
|[replace_filename](#replace_filename)|RReplaces 檔案名。|
|[root_directory](#root_directory)|傳回的`myname`根目錄元件。 |
|[root_name](#root_name)|傳回的根名稱元件`myname`。 |
|[root_path](#root_path)|傳回的`myname`根路徑元件。|
|[stem](#stem)|`stem`傳回的`myname`元件。|
|[string](#string)|轉換中`mypath`儲存的序列。|
|[swap](#swap)|執行`swap(mypath, right.mypath)`。|
|[u16string](#u16string)|將儲存在中`mypath`的序列轉換成 utf-16, 並傳回它儲存在類型`u16string`的物件中。|
|[u32string](#u32string)|將儲存在中`mypath`的序列轉換成 UTF-32, 並傳回儲存在類型`u32string`之物件中的順序。|
|[u8string](#u8string)|將儲存在中`mypath`的序列轉換成 utf-8, 並傳回它儲存在類型`u8string`的物件中。|
|[value_type](#value_type)|此類型描述主機作業系統偏好的路徑元素。|
|[wstring](#wstring)|將儲存在中`mypath`的序列轉換成主機系統針對序列所採用`wchar_t`的編碼, 並傳回它儲存在類型`wstring`的物件中。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_as)|以另一個路徑的複本取代路徑的元素。|
|[operator+=](#op_add)|各種`concat`運算式。|
|[operator/=](#op_divide)|各種`append`運算式。|
|[operator string_type](#op_string)|傳回 `myname`。|

## <a name="requirements"></a>需求

**標頭:** \<filesystem >

**命名空間：** std::experimental::filesystem

## <a name="append"></a>path:: append

視需要將指定的`mypath`序列附加至、轉換和插入。 `preferred_separator`

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*來源*\
指定的順序。

*頭*\
開始指定的順序。

*次*\
指定序列的結尾。

## <a name="assign"></a>path:: assign

取代`mypath`為指定的序列, 視需要進行轉換。

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*來源*\
指定的順序。

*頭*\
開始指定的順序。

*次*\
指定序列的結尾。

## <a name="begin"></a>path:: begin

傳回, `path::iterator`指定路徑名稱中的第一個路徑元素 (如果有的話)。

```cpp
iterator begin() const;
```

## <a name="c_str"></a>path:: c_str

傳回中`mypath`第一個字元的指標。

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a>path:: clear

執行`mypath.clear()`。

```cpp
void clear() noexcept;
```

## <a name="compare"></a>path:: compare

第一個函式會傳回 `mypath.compare(pval.native())`。 第二個函式會傳回 `mypath.compare(str)`。 第三個`mypath.compare(ptr)`函式會傳回。

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

*指標*\
要比較的指標。

## <a name="concat"></a>path:: concat

視需要將指定的`mypath`序列附加至、轉換 (但不插入分隔符號)。

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*來源*\
指定的順序。

*頭*\
開始指定的順序。

*次*\
指定序列的結尾。

## <a name="const_iterator"></a>path:: const_iterator

`iterator` 的同義字。

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>path:: empty

傳回 `mypath.empty()`。

```cpp
bool empty() const noexcept;
```

## <a name="end"></a>path:: end

傳回類型`iterator`的結束序列反覆運算器。

```cpp
iterator end() const;
```

## <a name="extension"></a>path:: extension

傳回的尾碼`filename()`。

```cpp
path extension() const;
```

### <a name="remarks"></a>備註

傳回的尾碼`filename() X` , 如下所示:

如果`X == path(".") || X == path("..")`或如果`X`不包含任何點, 則尾碼會是空的。

否則後置詞開頭 (並包含) 會是最右邊的點。

## <a name="filename"></a>path:: filename

傳回 myname 的根目錄元件，即 `empty() path() : *--end()`。 元件可能是空的。

```cpp
path filename() const;
```

## <a name="generic_string"></a>path:: generic_string

傳回 `this->string<Elem, Traits, Alloc>(al)` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a>path:: generic_u16string

傳回 `u16string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a>path:: generic_u32string

傳回 `u32string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a>path:: generic_u8string

傳回 `u8string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a>path:: generic_wstring

傳回 `wstring()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a>path:: has_extension

傳回 `!extension().empty()`。

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a>path:: has_filename

傳回 `!filename().empty()`。

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a>path:: has_parent_path

傳回 `!parent_path().empty()`。

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a>path:: has_relative_path

傳回 `!relative_path().empty()`。

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a>path:: has_root_directory

傳回 `!root_directory().empty()`。

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>path:: has_root_name

傳回 `!root_name().empty()`。

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a>path:: has_root_path

傳回 `!root_path().empty()`。

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>path:: has_stem

傳回 `!stem().empty()`。

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>path:: is_absolute

若為 Windows, 此`has_root_name() && has_root_directory()`函式會傳回。 若為 Posix, `has_root_directory()`函式會傳回。

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>path:: is_relative

傳回 `!is_absolute()`。

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>path:: iterator

雙向常數反覆運算器, 指定的路徑元件`myname`。

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

類別會描述雙向常數反覆運算器, 其會`path`指定序列`myname`中的元件:

1. 根名稱，如果有的話

1. 根目錄，如果有的話

1. 父系`path`的其餘目錄元素 (如果有的話), 以檔案名結尾 (如果有的話)

針對`pval` 類型`path`為的物件:

1. `path::iterator X = pval.begin()`指定路徑名稱`path`中的第一個元素 (如果有的話)。

1. `X == pval.end()`當點剛好`X`超過元件序列結尾時為 true。

3. `*X`傳回符合目前元件的字串

1. 如果有的話，`++X` 會指定順序中的下一個元件。

1. 如果有的話，`--X` 會指定順序中的上一個元件。

1. 改變`myname`會使在中指定元素`myname`的所有反覆運算器失效。

## <a name="make_preferred"></a>path:: make_preferred

`preferred_separator`視需要將每個分隔符號轉換成。

```cpp
path& make_preferred();
```

## <a name="native"></a>path:: native

傳回 `myname`。

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a>path:: operator =

以另一個路徑的複本取代路徑的元素。

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>參數

*再*\
要[](../standard-library/path-class.md)複製到`path`中的路徑。

*來源*\
來源路徑。

### <a name="remarks"></a>備註

第一個成員運算子會`right.myname`將`myname`複製到。 第二個成員運算子`right.myname`會`myname`移至。 第三個成員運算子的行為與`*this = path(source)`相同。

## <a name="op_add"></a>path:: operator + =

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

*再*\
新增的路徑。

*str*\
新增的字串。

*指標*\
新增的指標。

*elem*\
新增`value_type`的或`Elem`。

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

## <a name="op_divide"></a>path:: operator/=

各種`append`運算式。

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>參數

*再*\
新增的路徑。

*來源*\
新增的來源。

### <a name="remarks"></a>備註

成員函式的行為與下列對應的運算式相同：

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a>path:: operator string_type

傳回 `myname`。

```cpp
operator string_type() const;
```

## <a name="parent_path"></a>路徑::p arent_path

傳回的`myname`父路徑元件。

```cpp
path parent_path() const;
```

### <a name="remarks"></a>備註

傳回的父路徑元件`myname`, 特別是移除`filename().native()`後的`myname`前置詞, 以及任何緊接在的目錄分隔符號。 (同樣地, `begin() != end()`如果是, 則會藉由連續`operator/=`套用來結合`[begin(), --end())`範圍中的所有元素)。元件可能是空的。

## <a name="path"></a>路徑::p 路徑 a)

`path`以各種方式來構造。

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

*再*\
結構的路徑, 即為複本。

*來源*\
結構化路徑是複本的來源。

*loc*\
指定的地區設定。

*頭*\
要複製之第一個元素的位置。

*次*\
要複製之最後一個元素的位置。

### <a name="remarks"></a>備註

所有的函式`myname`都會以各種方式進行結構:

`path()` 其`myname()`為。

適用`path(const path& right`于) `myname(right.myname)`。

`path(path&& right)` 其`myname(right.myname)`為。

`template<class Source> path(const Source& source)` 其`myname(source)`為。

針對`template<class Source> path(const Source& source, const locale& loc)` 此`myname(source)`,從`loc`取得所需的 codecvt facet。

`template<class InIt> path(InIt first, InIt last)` 其`myname(first, last)`為。

針對`template<class InIt> path(InIt first, InIt last, const locale& loc)` 此`myname(first, last)`,從`loc`取得所需的 codecvt facet。

## <a name="preferred_separator"></a>路徑::p referred_separator

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

## <a name="relative_path"></a>path:: relative_path

傳回的`myname`相對路徑元件。

```cpp
path relative_path() const;
```

### <a name="remarks"></a>備註

傳回的相對路徑元件`myname`, 特別是移除`root_path().native()`後的`myname`尾碼, 以及任何立即後續的重複目錄分隔符號。 元件可能是空的。

## <a name="remove_filename"></a>path:: remove_filename

移除檔案名。

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a>path:: replace_extension

取代的延伸`myname`模組。

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>參數

*newext*\
新的延伸模組。

### <a name="remarks"></a>備註

先從`extension().native()` `myname`移除尾碼。 然後, `!newext.empty() && newext[0] != dot`如果 ( `dot`其中`*path(".").c_str()`是), `dot`則會將`myname`附加至。 然後, *newext*會附加`myname`至。

## <a name="replace_filename"></a>path:: replace_filename

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

## <a name="root_directory"></a>path:: root_directory

傳回的`myname`根目錄元件。

```cpp
path root_directory() const;
```

### <a name="remarks"></a>備註

元件可能是空的。

## <a name="root_name"></a>path:: root_name

傳回的根名稱元件`myname`。

```cpp
path root_name() const;
```

### <a name="remarks"></a>備註

元件可能是空的。

## <a name="root_path"></a>path:: root_path

傳回的`myname`根路徑元件。

```cpp
path root_path() const;
```

### <a name="remarks"></a>備註

傳回的根路徑元件`myname`, 特別是。 `root_name()`  /  `root_directory` 元件可能是空的。

## <a name="stem"></a>path:: 詞幹

`stem`傳回的`myname`元件。

```cpp
path stem() const;
```

### <a name="remarks"></a>備註

`filename().native()` `extension().native()`傳回的`stem`元件, 特別是移除任何結尾的。 `myname` 元件可能是空的。

## <a name="string"></a>path:: string

轉換中`mypath`儲存的序列。

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>備註

第一個 (範本) 成員函式會以`mypath`下列方式轉換儲存的序列:

1. `string()` 的 `string<char, Traits, Alloc>()`

1. `wstring()` 的 `string<wchar_t, Traits, Alloc>()`

1. `u16string()` 的 `string<char16_t, Traits, Alloc>()`

1. `u32string()` 的 `string<char32_t, Traits, Alloc>()`

第二個成員函式會將儲存`mypath`在中的序列轉換成主機系統針對**char**序列所採用的編碼, 並傳回它儲存在`string`類型的物件中。

## <a name="string_type"></a>path:: string_type

此類型是 `basic_string<value_type>` 的同義字。

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a>path:: swap

執行`swap(mypath, right.mypath)`。

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a>path:: u16string

將儲存在中`mypath`的序列轉換成 utf-16, 並傳回它儲存在類型`u16string`的物件中。

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>path:: u32string

將儲存在中`mypath`的序列轉換成 UTF-32, 並傳回儲存在類型`u32string`之物件中的順序。

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>path:: u8string

將儲存在中`mypath`的序列轉換成 utf-8, 並傳回它儲存在類型`u8string`的物件中。

```cpp
string u8string() const;
```

## <a name="value_type"></a>path:: value_type

此類型描述主機`path`作業系統所優先的元素。

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a>path:: wstring

將儲存在中`mypath`的序列轉換成主機系統針對**wchar_t**序列所採用的編碼, 並傳回它儲存在類型`wstring`的物件中。

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
