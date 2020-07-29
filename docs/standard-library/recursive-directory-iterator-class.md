---
title: recursive_directory_iterator 類別
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 0f9bdc3edd7f5798afaa8d170adc35708a6aafa2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217619"
---
# <a name="recursive_directory_iterator-class"></a>recursive_directory_iterator 類別

描述輸入反覆運算器，其會將目錄中的檔案名進行序列處理，可能會以遞迴方式遞減為子目錄。 若為 iterator `X` ，運算式 `*X` 會評估為類別的物件 `directory_entry` ，其會包裝檔案名和任何已知的狀態。

如需詳細資訊和程式碼範例，請參閱[檔案系統導覽（c + +）](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>備註

類別範本會儲存：

1. 類型的物件 `stack<pair<directory_iterator, path>>` ， `mystack` 針對展示的目的在此呼叫，這代表要排序的目錄的嵌套

1. `directory_entry`在這裡呼叫類型的物件 `myentry` ，其代表目錄序列中的目前檔案名

1. 類型的物件 **`bool`** ， `no_push` 在此稱為，其會記錄是否已停用遞迴下降到子目錄中

1. 類型的物件 `directory_options` ， `myoptions` 在此稱為，其會記錄在結構中建立的選項

類型的預設結構化物件 `recursive_directory_entry` 具有在的結束序列反覆運算器 `mystack.top().first` ，代表序列結尾反覆運算器。 例如，假設目錄 `abc` 包含專案 `def` （目錄）、 `def/ghi` 和 `jkl` ，則程式碼會：

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

會以引數和呼叫 `path("abc/def/ghi")` 造訪 `path("abc/jkl")` 。 您可以透過兩種方式來限定目錄子樹的排序：

1. 只有當您 `recursive_directory_iterator` 使用 `directory_options` 值為的引數來建立時，才會掃描目錄符號 `directory_options::follow_directory_symlink` 。

1. 如果您呼叫， `disable_recursion_pending` 則在增量期間遇到的後續目錄將不會以遞迴方式掃描。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|建構 `recursive_directory_iterator`。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[豐富](#depth)|`mystack.size() - 1`會傳回，因此 `pval` 深度為零。|
|[disable_recursion_pending](#disable_recursion_pending)|儲存 **`true`** 在中 `no_push` 。|
|[increment](#increment)|依序前進到下一個檔案名。|
|[options](#options)|傳回 `myoptions`。|
|[提示](#pop)|傳回下一個物件。|
|[recursion_pending](#recursion_pending)|傳回 `!no_push`。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[operator！ =](#op_neq)|傳回 `!(*this == right)`。|
|[operator =](#op_as)|預設成員指派運算子會如預期般運作。|
|[operator = =](#op_eq)|**`true`** 只有在 **`*this`** 和*right*都是序列結尾反覆運算器，或兩者都不是序列結束反覆運算器時，才會傳回。|
|[操作](#op_multiply)|傳回 `myentry`。|
|[operator->](#op_cast)|傳回 `&**this`。|
|[operator + +](#op_increment)|遞增 `recursive_directory_iterator` 。|

## <a name="requirements"></a>需求

**標頭：**\<filesystem>

**命名空間：** std::tr2::sys

## <a name="recursive_directory_iteratordepth"></a><a name="depth"></a>recursive_directory_iterator：:d epth

`mystack.size() - 1`會傳回，因此 `pval` 深度為零。

```cpp
int depth() const;
```

## <a name="recursive_directory_iteratordisable_recursion_pending"></a><a name="disable_recursion_pending"></a>recursive_directory_iterator：:d isable_recursion_pending

儲存 **`true`** 在中 `no_push` 。

```cpp
void disable_recursion_pending();
```

## <a name="recursive_directory_iteratorincrement"></a><a name="increment"></a>recursive_directory_iterator：：遞增值

依序前進到下一個檔案名。

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>參數

*歐洲*\
指定的錯誤碼。

### <a name="remarks"></a>備註

此函式會嘗試前進到巢狀序列中的下一個檔案名稱。 如果成功，它會在中儲存該檔案名， `myentry` 否則會產生序列結尾反覆運算器。

## <a name="recursive_directory_iteratoroperator"></a><a name="op_neq"></a>recursive_directory_iterator：： operator！ =

傳回 `!(*this == right)`。

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*再*\
要比較的[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="recursive_directory_iteratoroperator"></a><a name="op_as"></a>recursive_directory_iterator：： operator =

預設成員指派運算子會如預期般運作。

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>參數

*recursive_directory_iterator*\
要[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)複製到中的 recursive_directory_iterator `recursive_directory_iterator` 。

## <a name="recursive_directory_iteratoroperator"></a><a name="op_eq"></a>recursive_directory_iterator：： operator = =

**`true`** 只有在 **`*this`** 和*right*都是序列結尾反覆運算器，或兩者都不是序列結束反覆運算器時，才會傳回。

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*再*\
要比較的[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="recursive_directory_iteratoroperator"></a><a name="op_multiply"></a>recursive_directory_iterator：： operator *

傳回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="recursive_directory_iteratoroperator-"></a><a name="op_cast"></a>recursive_directory_iterator：： operator->

傳回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="recursive_directory_iteratoroperator"></a><a name="op_increment"></a>recursive_directory_iterator：： operator + +

遞增 `recursive_directory_iterator` 。

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>參數

*int*\
指定的增量。

### <a name="remarks"></a>備註

第一個成員函式會呼叫 `increment()` ，然後傳回 **`*this`** 。 第二個成員函式會建立物件的複本、呼叫 `increment()` ，然後傳回復本。

## <a name="recursive_directory_iteratoroptions"></a><a name="options"></a>recursive_directory_iterator：： options

傳回 `myoptions`。

```cpp
directory_options options() const;
```

## <a name="recursive_directory_iteratorpop"></a><a name="pop"></a>recursive_directory_iterator：:p op

傳回下一個物件。

```cpp
void pop();
```

### <a name="remarks"></a>備註

如果 `depth() == 0` 物件成為序列的結尾反覆運算器，則為。 否則，此成員函式會終止掃描目前 (最深) 的目錄，並在次深的目錄繼續掃描。

## <a name="recursive_directory_iteratorrecursion_pending"></a><a name="recursion_pending"></a>recursive_directory_iterator：： recursion_pending

傳回 `!no_push`。

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iteratorrecursive_directory_iterator"></a><a name="recursive_directory_iterator"></a>recursive_directory_iterator：： recursive_directory_iterator

建構 `recursive_directory_iterator`。

```cpp
recursive_directory_iterator() noexcept;
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,
    error_code& ec) noexcept;
recursive_directory_iterator(const path& pval,
    directory_options opts);

recursive_directory_iterator(const path& pval,
    directory_options opts,
    error_code& ec) noexcept;
recursive_directory_iterator(const recursive_directory_iterator&) = default;
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>參數

*pval*\
指定的路徑。

*error_code*\
指定的錯誤碼。

*opts*\
指定的目錄選項。

*recursive_directory_iterator*\
要從中複製所建構之 `recursive_directory_iterator` 的 `recursive_directory_iterator`。

### <a name="remarks"></a>備註

第一個建構函式會產生序列結尾迭代器。 第二個和第三個函式會將儲存 **`false`** 在 `no_push` 和 `directory_options::none` 中 `myoptions` ，然後嘗試以目錄的形式開啟和讀取*pval* 。 如果成功，則會初始化 `mystack` 並 `myentry` 指定嵌套順序中的第一個非目錄檔案名，否則會產生結束序列反覆運算器。

第四個和第五個函式的行為與第二個和第三個相同，不同之處在于它們會*先儲存選擇* `myoptions` 。 預設建構函式會如預期般運作。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)
