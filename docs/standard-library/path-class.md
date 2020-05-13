---
title: path 類別
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 669dfd2c8cd8576ebfb6684bab7cf63cdd51babc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372112"
---
# <a name="path-class"></a>path 類別

**路徑**類別儲存類型的`string_type`物件 ,此`myname`處稱為 "公開",適合用作路徑名稱。 `string_type``basic_string<value_type>`是的同義詞,`value_type`其中是 windows 上**wchar_t**的同義字,或 POSIX 上的**字元**的同義詞。

如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class path;
```

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[路徑](#path)|建構 `path`。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[const_iterator](#const_iterator)|`iterator` 的同義字。|
|[反覆運算](#iterator)|指定的雙向常量反覆運算器,`path`用於指定`myname`的元件。|
|[string_type](#string_type)|這個類型與 `basic_string<value_type>`同義。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[附加](#append)|根據需要將指定的序列追加到`mypath`,並根據需要轉換並插入preferred_separator。|
|[配置](#assign)|`mypath`替換為指定的序列,根據需要轉換。|
|[開始](#begin)|返回指定`path::iterator`路徑名稱中的第一個路徑元素(如果存在)。|
|[c_str](#c_str)|返回指向 中第一個字元`mypath`的指標。|
|[清楚](#clear)|執行`mypath.clear()`。|
|[比較](#compare)|返回比較值。|
|[Concat](#compare)|根據需要將指定的序列追加到`mypath`轉換(但不插入分隔符)。|
|[空](#empty)|傳回 `mypath.empty()`。|
|[結束](#end)|返回類型`iterator`序列結束反覆運算器。|
|[延伸](#extension)|返回的`filename()`後綴。|
|[檔案名稱](#filename)|傳回 myname 的根目錄元件，即 `empty() path() : *--end()`。 元件可能是空的。|
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
|[is_absolute](#is_absolute)|對於 Windows,函數`has_root_name() && has_root_directory()`將傳回 。 對於 POSIX,函數`has_root_directory()`傳回 。|
|[is_relative](#is_relative)|傳回 `!is_absolute()`。|
|[make_preferred](#make_preferred)|根據需要將每個分隔符轉換為preferred_separator。|
|[本地端](#native)|傳回 `myname`。|
|[parent_path](#parent_path)|返回的`myname`父路徑元件。|
|[preferred_separator](#preferred_separator)|常數物件會提供慣用的字元分隔路徑元件，隨主機作業系統而異。 |
|[relative_path](#relative_path)|返回`myname`的相對路徑元件。 |
|[remove_filename](#remove_filename)|刪除檔名。|
|[replace_extension](#replace_extension)|替換的`myname`擴展。 |
|[replace_filename](#replace_filename)|R 替換檔名。|
|[root_directory](#root_directory)|傳回`myname`的 根目錄元件。 |
|[root_name](#root_name)|傳回`myname`的 根名稱元件。 |
|[root_path](#root_path)|返回的`myname`根路徑元件。|
|[莖](#stem)|返回`stem`的`myname`元件。|
|[string](#string)|轉換儲存在中的`mypath`序列。|
|[交換](#swap)|執行`swap(mypath, right.mypath)`。|
|[u16字串](#u16string)|將存儲在中的`mypath`序列轉換為 UTF-16,並將其返回存儲`u16string`在類型 物件中。|
|[u32string](#u32string)|將存儲在中的`mypath`序列轉換為 UTF-32,並將其返回存儲`u32string`在類型 物件中。|
|[u8 字串](#u8string)|將儲存在中的`mypath`序列轉換為 UTF-8,並將其返回存儲`u8string`在類型 物件中。|
|[value_type](#value_type)|此類型描述主機作業系統偏好的路徑元素。|
|[wstring](#wstring)|將儲存在中的`mypath`序列轉換為主機系統`wchar_t`對 序列所青睞的編碼,並將其返回存儲`wstring`在類型 物件中。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子*](#op_as)|將路徑的元素替換為另一個路徑的副本。|
|[運算子*](#op_add)|各種`concat`運算式。|
|[操作員/*](#op_divide)|各種`append`運算式。|
|[運算子string_type](#op_string)|傳回 `myname`。|

## <a name="requirements"></a>需求

**標題:**\<檔案系統>

**命名空間：** std::experimental::filesystem

## <a name="pathappend"></a><a name="append"></a>路徑::追加

根據需要指定的序列中,`mypath`並根據需要插入`preferred_separator`。

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*源*\
指定序列。

*第一*\
指定序列的開始。

*最後*\
指定序列的結束。

## <a name="pathassign"></a><a name="assign"></a>路徑::配置

`mypath`替換為指定的序列,根據需要轉換。

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*源*\
指定序列。

*第一*\
指定序列的開始。

*最後*\
指定序列的結束。

## <a name="pathbegin"></a><a name="begin"></a>路徑::開始

返回指定`path::iterator`路徑名稱中的第一個路徑元素(如果存在)。

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a>路徑::c_str

返回指向 中第一個字元`mypath`的指標。

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a>路徑::清除

執行`mypath.clear()`。

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a>路徑::比較

第一個函式會傳回 `mypath.compare(pval.native())`。 第二個函式會傳回 `mypath.compare(str)`。 第三個函數`mypath.compare(ptr)`傳回 。

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>參數

*普瓦爾*\
要比較的路徑。

*Str*\
要比較的字串。

*Ptr*\
要比較的指標。

## <a name="pathconcat"></a><a name="concat"></a>路徑::concat

根據需要將指定的序列追加到`mypath`轉換(但不插入分隔符)。

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>參數

*源*\
指定序列。

*第一*\
指定序列的開始。

*最後*\
指定序列的結束。

## <a name="pathconst_iterator"></a><a name="const_iterator"></a>路徑::const_iterator

`iterator` 的同義字。

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a>路徑::空

傳回 `mypath.empty()`。

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a>路徑::結束

返回類型`iterator`序列結束反覆運算器。

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a>路徑:延伸

返回的`filename()`後綴。

```cpp
path extension() const;
```

### <a name="remarks"></a>備註

返回以下項目的`filename() X`尾號::

如果`X == path(".") || X == path("..")``X`或 不包含點,則後綴為空。

否則後置詞開頭 (並包含) 會是最右邊的點。

## <a name="pathfilename"></a><a name="filename"></a>路徑::檔案名稱

傳回 myname 的根目錄元件，即 `empty() path() : *--end()`。 元件可能是空的。

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a>路徑::generic_string

傳回 `this->string<Elem, Traits, Alloc>(al)` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a>路徑::generic_u16string

傳回 `u16string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a>路徑::generic_u32string

傳回 `u32string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a>路徑::generic_u8string

傳回 `u8string()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a>路徑::generic_wstring

傳回 `wstring()` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a>路徑::has_extension

傳回 `!extension().empty()`。

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a>路徑::has_filename

傳回 `!filename().empty()`。

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a>路徑::has_parent_path

傳回 `!parent_path().empty()`。

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a>路徑::has_relative_path

傳回 `!relative_path().empty()`。

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a>路徑::has_root_directory

傳回 `!root_directory().empty()`。

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a>路徑::has_root_name

傳回 `!root_name().empty()`。

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a>路徑::has_root_path

傳回 `!root_path().empty()`。

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a>路徑::has_stem

傳回 `!stem().empty()`。

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a>路徑::is_absolute

對於 Windows,函數`has_root_name() && has_root_directory()`將傳回 。 對於 POSIX,函數`has_root_directory()`傳回 。

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a>路徑::is_relative

傳回 `!is_absolute()`。

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a>路徑:反覆發器

指定的雙向常量反覆運算器,用於指定`myname`的 路徑元件。

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

類別描述一個雙向常巧式, 以序列`path`中指定`myname`的元件:

1. 根名稱，如果有的話

1. 根目錄，如果有的話

1. 父`path`目錄元素(如果存在)以檔案名結尾(如果存在)

對`pval`類型`path`的物件:

1. `path::iterator X = pval.begin()`指定路徑名稱中`path`的第一個元素(如果存在)。

1. `X == pval.end()`當點剛剛`X`超過元件序列的末尾時,為 true。

1. `*X`傳回與目前元件比對字串

1. 如果有的話，`++X` 會指定順序中的下一個元件。

1. 如果有的話，`--X` 會指定順序中的上一個元件。

1. 更改`myname`會使指定元素`myname`的所有反覆運算器無效。

## <a name="pathmake_preferred"></a><a name="make_preferred"></a>路徑::make_preferred

根據需要將每個分隔符轉換為`preferred_separator`。

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a>路徑::本機

傳回 `myname`。

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a>路徑::運算符*

將路徑的元素替換為另一個路徑的副本。

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>參數

*對*\
複製到的[路徑](../standard-library/path-class.md) `path` 。

*源*\
源路徑。

### <a name="remarks"></a>備註

第一個成員運算子複製到`right.myname``myname`。 第二個成員運算子將`right.myname`移到`myname`。 第三個成員運算子的操作與 相同`*this = path(source)`。

## <a name="pathoperator"></a><a name="op_add"></a>路徑::運算符*

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

*對*\
添加的路徑。

*Str*\
新增的字串。

*Ptr*\
添加的指標。

*埃萊姆*\
新增`value_type`的`Elem`或 。

*源*\
添加的源。

### <a name="remarks"></a>備註

成員函式的行為與下列對應的運算式相同：

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="pathoperator"></a><a name="op_divide"></a>路徑::運算符/*

各種`append`運算式。

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>參數

*對*\
添加的路徑。

*源*\
添加的源。

### <a name="remarks"></a>備註

成員函式的行為與下列對應的運算式相同：

1. `append(right);`

1. `append(source);`

## <a name="pathoperator-string_type"></a><a name="op_string"></a>路徑::運算符string_type

傳回 `myname`。

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a>路徑::p

返回的`myname`父路徑元件。

```cpp
path parent_path() const;
```

### <a name="remarks"></a>備註

傳回`myname`的父路徑元件 ,`myname``filename().native()`特別是刪除 後和任何緊鄰目錄分隔符的前置碼。 (同樣,如果`begin() != end()`,它是通過連續`[begin(), --end())``operator/=`應用 () 來組合範圍內的所有元素。元件可能為空。

## <a name="pathpath"></a><a name="path"></a>路徑::p

以各種方式建構`path`。

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

*對*\
構造路徑為副本的路徑。

*源*\
構造路徑為副本的源。

*loc*\
指定的區域設置。

*第一*\
要複製之第一個元素的位置。

*最後*\
要複製的最後一個元素的位置。

### <a name="remarks"></a>備註

建構函數都以各種方式建構`myname`:

因為它是`path()``myname()`。

因為`path(const path& right``myname(right.myname)`) 它是 。

因為它是`path(path&& right)``myname(right.myname)`。

因為它是`template<class Source> path(const Source& source)``myname(source)`。

因為它是`template<class Source> path(const Source& source, const locale& loc)``myname(source)`,`loc`從 獲取任何所需的編解碼法分面。

因為它是`template<class InIt> path(InIt first, InIt last)``myname(first, last)`。

因為它是`template<class InIt> path(InIt first, InIt last, const locale& loc)``myname(first, last)`,`loc`從 獲取任何所需的編解碼法分面。

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a>路徑::p引用分離器

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

## <a name="pathrelative_path"></a><a name="relative_path"></a>路徑::relative_path

返回`myname`的相對路徑元件。

```cpp
path relative_path() const;
```

### <a name="remarks"></a>備註

傳回的相對路徑元件`myname`,特別是`root_path().native()`刪除 後的`myname`任何後續冗 餘目錄分隔符的後綴。 元件可能是空的。

## <a name="pathremove_filename"></a><a name="remove_filename"></a>路徑::remove_filename

刪除檔名。

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a>路徑::replace_extension

替換的`myname`擴展。

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>參數

*紐埃斯特*\
新的擴展。

### <a name="remarks"></a>備註

先從`myname`中移除後置`extension().native()`字串 。 然後,`!newext.empty() && newext[0] != dot`如果`dot`(`*path(".").c_str()`位置`dot`),`myname`則附加到 。 然後 *,將 newext*`myname`附加到 。

## <a name="pathreplace_filename"></a><a name="replace_filename"></a>路徑::replace_filename

替換檔名。

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>參數

*普瓦爾*\
檔名的路徑。

### <a name="remarks"></a>備註

成員函式會執行：

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathroot_directory"></a><a name="root_directory"></a>路徑::root_directory

傳回`myname`的 根目錄元件。

```cpp
path root_directory() const;
```

### <a name="remarks"></a>備註

元件可能是空的。

## <a name="pathroot_name"></a><a name="root_name"></a>路徑::root_name

傳回`myname`的 根名稱元件。

```cpp
path root_name() const;
```

### <a name="remarks"></a>備註

元件可能是空的。

## <a name="pathroot_path"></a><a name="root_path"></a>路徑::root_path

返回的`myname`根路徑元件。

```cpp
path root_path() const;
```

### <a name="remarks"></a>備註

傳回的根路徑元件`myname`,`root_name()` / `root_directory`具體 。 元件可能是空的。

## <a name="pathstem"></a><a name="stem"></a>路徑:stem

返回`stem`的`myname`元件。

```cpp
path stem() const;
```

### <a name="remarks"></a>備註

傳`stem`回`myname`的元件,特別是`filename().native()`刪除任何尾隨`extension().native()`的元件。 元件可能是空的。

## <a name="pathstring"></a><a name="string"></a>路徑:字串

轉換儲存在中的`mypath`序列。

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>備註

第一個(樣本)成員函數以與以下方式轉換`mypath`儲存的序列:

1. `string()` 為 `string<char, Traits, Alloc>()`

1. `wstring()` 為 `string<wchar_t, Traits, Alloc>()`

1. `u16string()` 為 `string<char16_t, Traits, Alloc>()`

1. `u32string()` 為 `string<char32_t, Traits, Alloc>()`

第二個成員函數將存儲在中的`mypath`序列轉換為主機系統為**字元**序列所青睞的編碼,並將其返回存儲`string`在類型 物件中。

## <a name="pathstring_type"></a><a name="string_type"></a>路徑::string_type

這個類型與 `basic_string<value_type>`同義。

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a>路徑::交換

執行`swap(mypath, right.mypath)`。

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a>路徑::u16字串

將存儲在中的`mypath`序列轉換為 UTF-16,並將其返回存儲`u16string`在類型 物件中。

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a>路徑::u32字串

將存儲在中的`mypath`序列轉換為 UTF-32,並將其返回存儲`u32string`在類型 物件中。

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a>路徑::u8字串

將儲存在中的`mypath`序列轉換為 UTF-8,並將其返回存儲`u8string`在類型 物件中。

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a>路徑::value_type

類型描述主機作業系統`path`青睞的元素。

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a>路徑::wstring

將儲存在中的`mypath`序列轉換為主機系統對**wchar_t**序列所青睞的編碼,並將其返回`wstring`存儲在類型 物件中。

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
