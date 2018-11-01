---
title: directory_entry 類別
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- filesystem/std::experimental::filesystem::directory_entry::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator=
- filesystem/std::experimental::filesystem::directory_entry::assign
- filesystem/std::experimental::filesystem::directory_entry::replace_filename
- filesystem/std::experimental::filesystem::directory_entry::path
- filesystem/std::experimental::filesystem::directory_entry::status
- filesystem/std::experimental::filesystem::directory_entry::symlink_status
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;
- filesystem/std::experimental::filesystem::directory_entry::operator==
- filesystem/std::experimental::filesystem::directory_entry::operator!=
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;=
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;=
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
helpviewer_keywords:
- std::experimental::filesystem::directory_entry
- std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- std::experimental::filesystem::directory_entry::directory_entry
- std::experimental::filesystem::directory_entry::operator=
- std::experimental::filesystem::directory_entry::assign
- std::experimental::filesystem::directory_entry::replace_filename
- std::experimental::filesystem::directory_entry::path
- std::experimental::filesystem::directory_entry::status
- std::experimental::filesystem::directory_entry::symlink_status
- std::experimental::filesystem::directory_entry::operator&lt;
- std::experimental::filesystem::directory_entry::operator==
- std::experimental::filesystem::directory_entry::operator!=
- std::experimental::filesystem::directory_entry::operator&lt;=
- std::experimental::filesystem::directory_entry::operator&gt;
- std::experimental::filesystem::directory_entry::operator&gt;=
ms.openlocfilehash: c1b68aefd44d8f0ac60c36307dee93333d801bb9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533818"
---
# <a name="directoryentry-class"></a>directory_entry 類別

描述 `*X` 所傳回的物件，其中 *X* 是 [directory_iterator](../standard-library/directory-iterator-class.md) 或 [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)。

## <a name="syntax"></a>語法

```cpp
class directory_entry;
```

## <a name="remarks"></a>備註

此類別會儲存 [path](../standard-library/path-class.md) 類型的物件。 預存的 `path` 可以是 [path 類別](../standard-library/path-class.md)的執行個體，或衍生自 `path` 之類型的執行個體。 它也會儲存兩個 [file_type](../standard-library/filesystem-enumerations.md#file_type) 值；一個代表已知的預存檔案名稱狀態，另一個則代表已知檔案名稱的符號連結狀態。

如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[directory_entry](#directory_entry)|預設建構函式會如預期般運作。 第四個建構函式初始化`mypath`要*pval*，`mystat`來*stat_arg*，和`mysymstat`至*symstat_arg*。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[assign](#assign)|此成員函式會指派*pval*要`mypath`， *stat*來`mystat`，和*將 symstat 指派*來`mysymstat`。|
|[path](#path)|成員函式會傳回 `mypath`。|
|[replace_filename](#replace_filename)|成員函式會取代`mypath`與`mypath.parent_path()`  /  *pval*，`mystat`與*stat_arg*，以及`mysymstat`與*取代 mysymstat*|
|[status](#status)|這兩個成員函式會傳回`mystat`第一個可能修改。|
|[symlink_status](#symlink_status)|這兩個成員函式會傳回`mysymstat`第一個可能修改。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](#op_neq)|用另一個清單複本取代清單的元素。|
|[operator=](#op_as)|預設成員指派運算子會如預期般運作。|
|[operator==](#op_eq)|傳回 `mypath == right.mypath`。|
|[operator<](#op_lt)|傳回 `mypath < right.mypath`。|
|[operator<=](#op_lteq)|傳回 `!(right < *this)`。|
|[operator>](#op_gt)|傳回 `right < *this`。|
|[operator>=](#op_gteq)|傳回 `!(*this < right)`。|
|[運算子 const path_type&amp （& s)](#path_type)|傳回 `mypath`。|

## <a name="requirements"></a>需求

**標頭：** \<experimental/filesystem>&gt;

**命名空間：** std::experimental::filesystem

## <a name="assign"></a> 指派

此成員函式會指派*pval*要`mypath`， *stat_arg*來`mystat`，和*symstat_arg*到`mysymstat`。

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>參數

*pval*<br/>
儲存的檔案名稱路徑。

*取代 mystat*<br/>
預存的檔案名稱的狀態。

*取代 mysymstat*<br/>
儲存的檔案名稱符號連結狀態。

## <a name="directory_entry"></a> directory_entry

預設建構函式會如預期般運作。 第四個建構函式初始化`mypath`要*pval*，`mystat`來*stat_arg*，和`mysymstat`至*symstat_arg*。

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>參數

*pval*<br/>
儲存的檔案名稱路徑。

*取代 mystat*<br/>
預存的檔案名稱的狀態。

*取代 mysymstat*<br/>
儲存的檔案名稱符號連結狀態。

## <a name="op_neq"></a> 運算子 ！ =

成員函式會傳回 `!(*this == right)`。

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)比較`directory_entry`。

## <a name="op_as"></a> 運算子 =

預設成員指派運算子會如預期般運作。

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>參數

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)複製到`directory_entry`。

## <a name="op_eq"></a> 運算子 = =

成員函式會傳回 `mypath == right.mypath`。

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)比較`directory_entry`。

## <a name="op_lt"></a> 運算子&lt;

成員函式會傳回 `mypath < right.mypath`。

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)比較`directory_entry`。

## <a name="op_lteq"></a> 運算子&lt;=

成員函式會傳回 `!(right < *this)`。

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)比較`directory_entry`。

## <a name="op_gt"></a> 運算子&gt;

成員函式會傳回 `right < *this`。

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)比較`directory_entry`。

## <a name="op_gteq"></a> 運算子&gt;=

成員函式會傳回 `!(*this < right)`。

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)比較`directory_entry`。

## <a name="path_type"></a> 運算子 const path_type&amp （& s)

此成員運算子會傳回 `mypath`。

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a> 路徑

成員函式會傳回 `mypath`。

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a> replace_filename

成員函式會取代`mypath`與`mypath.parent_path()`  /  *pval*，`mystat`與*stat_arg*，以及`mysymstat`與*取代 mysymstat*

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>參數

*pval*<br/>
儲存的檔案名稱路徑。

*取代 mystat*<br/>
預存的檔案名稱的狀態。

*取代 mysymstat*<br/>
儲存的檔案名稱符號連結狀態。

## <a name="status"></a> 狀態

這兩個成員函式會傳回`mystat`第一個可能修改，如下所示：

1. 如果`status_known(mystat)`不執行任何動作。

1. 否則，如果`!status_known(mysymstat) && !is_symlink(mysymstat)`然後`mystat = mysymstat`。

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>參數

*ec*<br/>
狀態錯誤程式碼。

## <a name="symlink_status"></a> symlink_status

這兩個成員函式會傳回`mysymstat`第一個可能修改，如下所示： 如果`status_known(mysymstat)`不執行任何動作。 否則為 `mysymstat = symlink_status(mypval)`。

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>參數

*ec*<br/>
狀態錯誤程式碼。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem&gt;](../standard-library/filesystem.md)<br/>
