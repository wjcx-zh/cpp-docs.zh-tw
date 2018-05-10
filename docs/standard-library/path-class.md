---
title: path 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 8ea20d43e2679addc10465cfc549a64fc210274f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="path-class"></a>path 類別

**path** 類別會儲存類型 string\_type 的物件 (這裡基於示範目的而稱為 myname)，適合用於路徑名稱。 string\_type 與 basic\_string\<value_type> 同義，其中 value\_type 與 Windows 下的 char 或 Posix 下的 wchar_t 同義。

如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class path;
```

## <a name="pathappend"></a>path::append

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

成員函式將指定的序列加在 mypath 的後面，視需要轉換並插入 preferred_separator。

## <a name="pathassign"></a>path::assign

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

成員函式會以指定的序列取代 mypath，視需要轉換。

## <a name="pathbegin"></a>path::begin

```cpp
iterator begin() const;
```

傳回指定路徑名稱中第一個路徑元素的 path::iterator，如果有的話。

## <a name="pathcstr"></a>path::c_str

```cpp
const value_type& *c_str() const noexcept;
```

傳回 mypath 第一個字元的指標。

## <a name="pathclear"></a>path::clear

```cpp
void clear() noexcept;
```

成員函式會執行 mypath.clear()。

## <a name="pathcompare"></a>path::compare

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

第一個函式會傳回 mypath.compare(pval.native())。 第二個函式會傳回 mypath.compare(str)。 第三個函式會傳回 mypath.compare(ptr)。

## <a name="pathconcat"></a>path::concat

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

成員函式將指定的序列加在 mypath 的後面，視需要轉換，但不插入分隔符號。

## <a name="pathconstiterator"></a>path::const_iterator

```cpp
typedef iterator const_iterator;
```

這個類型是迭代器的同義字。

## <a name="pathempty"></a>path::empty

```cpp
bool empty() const noexcept;
```

傳回 mypath.empty()。

## <a name="pathend"></a>path::end

```cpp
iterator end() const;
```

傳回類型迭代器的序列結尾迭代器。

## <a name="pathextension"></a>path::extension

```cpp
path extension() const;
```

傳回的 filename() X 的後置詞，像這樣：

如果 X == path(".") &#124;&#124; X == path("..")，或如果 X 沒有點，後置詞就是空的。

否則後置詞開頭 (並包含) 會是最右邊的點。

## <a name="pathfilename"></a>path::filename

```cpp
path filename() const;
```

傳回 myname 的根目錄元件，即 `empty()  path() : *--end()`。 元件可能是空的。

## <a name="pathgenericstring"></a>path::generic_string

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

傳回 `this->string<Elem, Traits, Alloc>(al)` 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

## <a name="pathgenericu16string"></a>path::generic_u16string

```cpp
u16string generic_u16string() const;
```

傳回 u16string() 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

## <a name="pathgenericu32string"></a>path::generic_u32string

```cpp
u32string generic_u32string() const;
```

傳回 u32string() 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

## <a name="pathgenericu8string"></a>path::generic_u8string

```cpp
string generic_u8string() const;
```

傳回 u8string() 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

## <a name="pathgenericwstring"></a>path::generic_wstring

```cpp
wstring generic_wstring() const;
```

傳回 wstring() 並 (在 Windows 下) 將任何反斜線轉換成正斜線。

## <a name="pathhasextension"></a>path::has_extension

```cpp
bool has_extension() const;
```

傳回 !extension().empty()。

## <a name="pathhasfilename"></a>path::has_filename

```cpp
bool has_filename() const;
```

傳回 !filename().empty()。

## <a name="pathhasparentpath"></a>path::has_parent_path

```cpp
bool has_parent_path() const;
```

傳回 !parent_path().empty()。

## <a name="pathhasrelativepath"></a>path::has_relative_path

```cpp
bool has_relative_path() const;
```

傳回 !relative_path().empty()。

## <a name="pathhasrootdirectory"></a>path::has_root_directory

```cpp
bool has_root_directory() const;
```

傳回 !root_directory().empty()。

## <a name="pathhasrootname"></a>path::has_root_name

```cpp
bool has_root_name() const;
```

傳回 !root_name().empty()。

## <a name="pathhasrootpath"></a>path::has_root_path

```cpp
bool has_root_path() const;
```

傳回 !root_path().empty()。

## <a name="pathhasstem"></a>path::has_stem

```cpp
bool has_stem() const;
```

傳回 !stem().empty()。

## <a name="pathisabsolute"></a>path::is_absolute

```cpp
bool is_absolute() const;
```

如為 Windows，函式會傳回 has_root_name() && has_root_directory()。 如為 Posix，函式會傳回 has_root_directory()。

## <a name="pathisrelative"></a>path::is_relative

```cpp
bool is_relative() const;
```

傳回 !is_absolute()。

## <a name="pathiterator"></a>path::iterator

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

此類別會描述雙向常數迭代器，指定序列中的 myname 路徑元件：

1. 根名稱，如果有的話

1. 根目錄，如果有的話

1. 父路徑的其餘目錄項目 (如果有的話)，以檔案名稱結尾，(如果有的話)

若為 pval，則為類型路徑的 物件：

1. path::iterator X = pval.begin() 指定路徑名稱中的第一個路徑元素，如果有的話。

1. 當 X 點剛好超過元件的序列結尾時，X == pval.end() 為 true。

3. *X 會傳回符合目前元件的字串。

1. 如果有的話，++X 會指定順序中的下一個元件。

1. 如果有的話，--X 會指定順序中的上一個元件。

1. 改變 myname 會使得所有指定 myname 元素的迭代器失效。

## <a name="pathmakepreferred"></a>path::make_preferred

```cpp
path& make_preferred();
```

成員函式會視需要將每個分隔符號轉換成 preferred_separator。

## <a name="pathnative"></a>path::native

```cpp
const string_type& native() const noexcept;
```

傳回 myname。

## <a name="pathoperator"></a>path::operator=

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

第一個成員運算子將 right.myname 複製到 myname。 第二個成員運算子將 right.myname 移至 myname。 第三個成員運算子的行為與 *this = path(source) 相同。

## <a name="pathoperator"></a>path::operator+=

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

成員函式的行為與下列對應的運算式相同：

1. concat(right);

1. concat(path(str));

1. concat(ptr);

1. concat(string_type(1, elem));

1. concat(source);

1. concat(path(basic_string\<Elem>(1, elem)));

## <a name="pathoperator"></a>path::operator/=

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

成員函式的行為與下列對應的運算式相同：

1. append(right);

1. append(source);

## <a name="pathoperator-stringtype"></a>path::operator string_type

```cpp
operator string_type() const;
```

成員運算子會傳回 myname。

## <a name="pathparentpath"></a>path::parent_path

```cpp
path parent_path() const;
```

傳回 myname 的父路徑元件，即移除 filename().native() 和任何緊鄰在前的目錄分隔符號之後的 myname 前置詞。 (同樣地，如果 begin() != end()，就是連續套用 operator/= 得到的 range [begin(), --end()) 所有元素的組合。)元件可能是空的。

## <a name="pathpath"></a>path::path

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

以各種方式建構 myname 的所有建構函式：

如為 path()，即是 myname()。

如為 path(const path& right)，即是 myname(right.myname)。

如為 path(path&& right)，即是 myname(right.myname)。

如為 template\<class Source> path(const Source& source)，即是 myname(source)。

如為 template\<class Source> path(const Source& source, const locale& loc)，即是 myname(source)，從 loc 取得任何需要的 codecvt Facet。

如為 template\<class InIt> path(InIt first, InIt last)，即是 myname(first, last)。

如為 template\<class InIt> path(InIt first, InIt last, const locale& loc)，即是 myname(first, last)，從 loc 取得任何需要的 codecvt Facet。

## <a name="pathpreferredseparator"></a>path::preferred_separator

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

常數物件會提供慣用的字元分隔路徑元件，隨主機作業系統而異。 請注意，Windows 大部分的內容同樣允許在這個位置使用 L'/'。

## <a name="pathrelativepath"></a>path::relative_path

```cpp
path relative_path() const;
```

傳回 myname 的相對路徑元件，即移除 root_path().native() 和任何緊鄰在後的備援目錄分隔符號之後的 myname 後置詞。 元件可能是空的。

## <a name="pathremovefilename"></a>path::remove_filename

```cpp
path& remove_filename();
```

## <a name="pathreplaceextension"></a>path::replace_extension

```cpp
path& replace_extension(const path& newext = path());
```

成員函式會先移除 myname 的後置詞 extension().native()。 然後，如果 !newext.empty() && newext[0] != dot (這裡的 dot 是 *path(".").c_str())，則會在 myname 後面加一點。 再將 newext 加到 myname 後面。

## <a name="pathreplacefilename"></a>path::replace_filename

```cpp
path& replace_filename(const path& pval);
```

成員函式會執行：

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathrootdirectory"></a>path::root_directory

```cpp
path root_directory() const;
```

傳回 myname 的根目錄元件。 元件可能是空的。

## <a name="pathrootname"></a>path::root_name

```cpp
path root_name() const;
```

傳回 myname 的根名稱元件。 元件可能是空的。

## <a name="pathrootpath"></a>path::root_path

```cpp
path root_path() const;
```

傳回 myname 的根路徑元件，即 root_name() / root_directory。 元件可能是空的。

## <a name="pathstem"></a>path::stem

```cpp
path stem() const;
```

傳回 myname 的主體元件，即移除了尾端 extension().native() 的 filename().native()。 元件可能是空的。

## <a name="pathstring"></a>path::string

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

第一個 (template) 成員函式會使用與下相同的方式轉換儲存在 mypath 的序列：

1. string() 用於 string\<char, Traits, Alloc>()

1. wstring() 用於 string\<wchar_t, Traits, Alloc>()

1. u16string() 用於 string\<char16_t, Traits, Alloc>()

1. u32string() 用於 string\<char32_t, Traits, Alloc>()

第二個成員函式會針對 char 序列，將儲存在 mypath 的序列轉換成主機系統偏好的編碼，並傳回儲存在類型 string 物件中。

## <a name="pathstringtype"></a>path::string_type

```cpp
typedef basic_string<value_type> string_type;
```

此類型是 basic_string<value_type> 的同義字。

## <a name="pathswap"></a>path::swap

```cpp
void swap(path& right) noexcept;
```

執行 swap(mypath, right.mypath)。

## <a name="pathu16string"></a>path::u16string

```cpp
u16string u16string() const;
```

成員函式會將儲存在 mypath 的序列轉換成 UTF-16，並傳回儲存在類型 u16string 物件中。

## <a name="pathu32string"></a>path::u32string

```cpp
u32string u32string() const;
```

成員函式會將儲存在 mypath 的序列轉換成 UTF-32，並傳回儲存在類型 u32string 物件中。

## <a name="pathu8string"></a>path::u8string

```cpp
string u8string() const;
```

成員函式會將儲存在 mypath 的序列轉換成 UTF-8，並傳回儲存在類型 u8string 物件中。

## <a name="pathvaluetype"></a>path::value_type

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

此類型描述主機作業系統偏好的路徑元素。

## <a name="pathwstring"></a>path::wstring

```cpp
wstring wstring() const;
```

針對 wchar_t 序列，將儲存在 mypath 的序列轉換成主機系統偏好的編碼，並傳回儲存在類型 wstring 物件中。

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：**std::experimental::filesystem

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
