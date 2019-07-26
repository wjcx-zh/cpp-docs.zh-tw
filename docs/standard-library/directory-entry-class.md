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
ms.openlocfilehash: 35b0dc55bf5db2f799d9ade28cd5968ceab3332b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458964"
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

|建構函式|說明|
|-|-|
|[directory_entry](#directory_entry)|預設建構函式會如預期般運作。 第四個函`mypath`式會將`mystat`初始化為*pval*、 `mysymstat` *stat_arg*和*symstat_arg*。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[assign](#assign)|此成員函式會將`mypath`pval 指派給`mystat`、 *stat*至和`mysymstat` *symstat* 。|
|[path](#path)|成員函式會傳回 `mypath`。|
|[replace_filename](#replace_filename)|此成員函式`mypath`會`mypath.parent_path()`以 / pval `mystat` 、 *stat_arg*和 `mysymstat` *symstat_arg*取代|
|[status](#status)|這兩個成員`mystat`函式會傳回可能第一次變更。|
|[symlink_status](#symlink_status)|這兩個成員`mysymstat`函式會傳回可能第一次變更。|

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
|[運算子 const path_type &](#path_type)|傳回 `mypath`。|

## <a name="requirements"></a>需求

**標頭:** \<實驗性/檔案系統&gt;

**命名空間：** std::experimental::filesystem

## <a name="assign"></a>值賦

此成員函式會將`mypath`pval 指派給`mystat`、 *stat_arg*至, `mysymstat`並將*symstat_arg*指派給。

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>參數

*pval*\
儲存的檔案名路徑。

*stat_arg*\
儲存檔案名稱的狀態。

*symstat_arg*\
儲存檔案名稱的符號連結狀態。

## <a name="directory_entry"></a>directory_entry

預設建構函式會如預期般運作。 第四個函`mypath`式會將`mystat`初始化為*pval*、 `mysymstat` *stat_arg*和*symstat_arg*。

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>參數

*pval*\
儲存的檔案名路徑。

*stat_arg*\
儲存檔案名稱的狀態。

*symstat_arg*\
儲存檔案名稱的符號連結狀態。

## <a name="op_neq"></a>operator! =

成員函式會傳回 `!(*this == right)`。

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*再*\
要`directory_entry`與相比較的[directory_entry](../standard-library/directory-entry-class.md) 。

## <a name="op_as"></a>operator =

預設成員指派運算子會如預期般運作。

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>參數

*再*\
要[](../standard-library/directory-entry-class.md)複製到`directory_entry`中的 directory_entry。

## <a name="op_eq"></a>operator = =

成員函式會傳回 `mypath == right.mypath`。

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*再*\
要`directory_entry`與相比較的[directory_entry](../standard-library/directory-entry-class.md) 。

## <a name="op_lt"></a> 運算子&lt;

成員函式會傳回 `mypath < right.mypath`。

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*再*\
要`directory_entry`與相比較的[directory_entry](../standard-library/directory-entry-class.md) 。

## <a name="op_lteq"></a>操作&lt;=

成員函式會傳回 `!(right < *this)`。

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*再*\
要`directory_entry`與相比較的[directory_entry](../standard-library/directory-entry-class.md) 。

## <a name="op_gt"></a> 運算子&gt;

成員函式會傳回 `right < *this`。

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*再*\
要`directory_entry`與相比較的[directory_entry](../standard-library/directory-entry-class.md) 。

## <a name="op_gteq"></a>操作&gt;=

成員函式會傳回 `!(*this < right)`。

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>參數

*再*\
要`directory_entry`與相比較的[directory_entry](../standard-library/directory-entry-class.md) 。

## <a name="path_type"></a>運算子 const path_type &

此成員運算子會傳回 `mypath`。

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a>路徑名

成員函式會傳回 `mypath`。

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a>replace_filename

此成員函式`mypath`會`mypath.parent_path()`以 / pval `mystat` 、 *stat_arg*和 `mysymstat` *symstat_arg*取代

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>參數

*pval*\
儲存的檔案名路徑。

*stat_arg*\
儲存檔案名稱的狀態。

*symstat_arg*\
儲存檔案名稱的符號連結狀態。

## <a name="status"></a>狀態

這兩個成員`mystat`函式會傳回第一次變更, 如下所示:

1. 如果`status_known(mystat)`這樣做, 則不執行任何動作。

1. 否則, 則`!status_known(mysymstat) && !is_symlink(mysymstat)`為`mystat = mysymstat`, 否則為。

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>參數

*歐洲*\
狀態錯誤碼。

## <a name="symlink_status"></a>symlink_status

這兩個成員`mysymstat`函式會傳回第一次變更, 如下所示:如果`status_known(mysymstat)`這樣做, 則不執行任何動作。 否則為 `mysymstat = symlink_status(mypval)`。

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>參數

*歐洲*\
狀態錯誤碼。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem&gt;](../standard-library/filesystem.md)
