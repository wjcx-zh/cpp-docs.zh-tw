---
title: directory_iterator 類別
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::increment
- filesystem/std::experimental::filesystem::directory_iterator::operator=
- filesystem/std::experimental::filesystem::directory_iterator::operator==
- filesystem/std::experimental::filesystem::directory_iterator::operator!=
- filesystem/std::experimental::filesystem::directory_iterator::operator*
- filesystem/std::experimental::filesystem::directory_iterator::operator-&gt;
- filesystem/std::experimental::filesystem::directory_iterator::operator++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
helpviewer_keywords:
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator-&gt;
- std::experimental::filesystem::directory_iterator::operator++
ms.openlocfilehash: a7ccc2a941da079e14092af5b81dc537db4a48c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215773"
---
# <a name="directory_iterator-class"></a>directory_iterator 類別

描述可循序遍訪目錄中的檔案名稱的輸入迭代器。 若為 iterator `X` ，運算式 `*X` 會評估為類別的物件 `directory_entry` ，其會包裝檔案名和任何已知的狀態。

此類別會儲存類型的物件 `path` ， `mydir` 在這裡針對展示的用途（代表要排序的目錄名稱）和名為的類型物件 `directory_entry` `myentry` （代表目錄序列中的目前檔案名）進行呼叫。 類型的預設結構化物件 `directory_entry` 具有空 `mydir` 的路徑名稱，而且代表序列的結尾反覆運算器。

例如，假設目錄中 `abc` 有專案 `def` 和 `ghi` ，則程式碼會：

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

將 `visit` 使用引數 `path("abc/def")` 和呼叫 `path("abc/ghi")` 。

如需詳細資訊和程式碼範例，請參閱[檔案系統導覽（c + +）](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class directory_iterator;
```

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[directory_iterator](#directory_iterator)|建立一個輸入反覆運算器，其會將目錄中的檔案名進行序列。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[increment](#increment)|嘗試前進到目錄中的下一個檔案名。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[operator！ =](#op_neq)|傳回 `!(*this == right)`。|
|[operator =](#op_as)|預設成員指派運算子會如預期般運作。|
|[operator = =](#op_eq)|**`true`** 只有在 **`*this`** 和*right*都是序列結尾反覆運算器，或兩者都不是序列結束反覆運算器時，才會傳回。|
|[操作](#op_star)|傳回 `myentry`。|
|[operator->](#op_cast)|傳回 `&**this`。|
|[operator + +](#op_increment)|呼叫 `increment()` ，然後傳回 **`*this`** 或複製物件、呼叫 `increment()` ，然後傳回復本。|

## <a name="requirements"></a>需求

**標頭：**\<experimental/filesystem>

**命名空間：** std::experimental::filesystem

## <a name="directory_iteratordirectory_iterator"></a><a name="directory_iterator"></a>directory_iterator：:d irectory_iterator

第一個建構函式會產生序列結尾迭代器。 第二個和第三個函式會將*pval*儲存在中 `mydir` ，然後嘗試以 `mydir` 目錄的形式開啟和讀取。 如果成功，則會在的目錄中儲存第一個檔案名， `myentry` 否則會產生結束序列反覆運算器。

預設建構函式會如預期般運作。

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>參數

*pval*\
儲存的檔案名路徑。

*歐洲*\
狀態錯誤碼。

*directory_iterator*\
儲存的物件。

## <a name="directory_iteratorincrement"></a><a name="increment"></a>directory_iterator：：遞增值

此函式會嘗試前進到目錄中的下一個檔案名稱。 如果成功，它會在中儲存該檔案名， `myentry` 否則會產生序列結尾反覆運算器。

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="directory_iteratoroperator"></a><a name="op_neq"></a>directory_iterator：： operator！ =

成員運算子會傳回 `!(*this == right)`。

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*再*\
要[directory_iterator](../standard-library/directory-iterator-class.md)與相比較的 directory_iterator `directory_iterator` 。

## <a name="directory_iteratoroperator"></a><a name="op_as"></a>directory_iterator：： operator =

預設成員指派運算子會如預期般運作。

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>參數

*再*\
要[directory_iterator](../standard-library/directory-iterator-class.md)複製到中的 directory_iterator `directory_iterator` 。

## <a name="directory_iteratoroperator"></a><a name="op_eq"></a>directory_iterator：： operator = =

**`true`** 只有當 **`*this`** 和*許可權*都是序列結尾反覆運算器，或兩者都不是序列結束反覆運算器時，此成員運算子才會傳回。

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*再*\
要[directory_iterator](../standard-library/directory-iterator-class.md)與相比較的 directory_iterator `directory_iterator` 。

## <a name="directory_iteratoroperator"></a><a name="op_star"></a>directory_iterator：： operator *

成員運算子會傳回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="directory_iteratoroperator-"></a><a name="op_cast"></a>directory_iterator：： operator->

成員函式會傳回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="directory_iteratoroperator"></a><a name="op_increment"></a>directory_iterator：： operator + +

第一個成員函式會呼叫 `increment()` ，然後傳回 **`*this`** 。 第二個成員函式會建立物件的複本、呼叫 `increment()` ，然後傳回復本。

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>參數

*int*\
遞增的數目。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)
