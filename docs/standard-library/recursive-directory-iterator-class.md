---
title: recursive_directory_iterator 類別
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: a5200c030986ebbcfccb1eba2963e8317c879eb6
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686796"
---
# <a name="recursive_directory_iterator-class"></a>recursive_directory_iterator 類別

描述輸入反覆運算器，其會將目錄中的檔案名進行序列處理，可能會以遞迴方式遞減為子目錄。 對於反覆運算器 `X`，運算式 `*X` 會評估為包裝檔案名的類別 `directory_entry` 物件，以及任何已知其狀態的專案。

如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>備註

類別範本會儲存：

1. `stack<pair<directory_iterator, path>>` 類型的物件，在此稱為 `mystack`，用於展示的用途，其代表要排序之目錄的嵌套

1. `directory_entry` 稱為 `myentry` 類型的物件，其代表目錄順序中目前的檔案名

1. 屬於**bool**類型的物件，在此稱為 `no_push`，這會記錄是否已停用遞迴下降到子目錄中

1. `directory_options` 類型的物件，稱為 `myoptions` 這裡，這會記錄在結構中建立的選項

@No__t_0 類型的預設結構化物件具有 `mystack.top().first` 的結尾反覆運算器，並代表序列結尾反覆運算器。 例如，假設目錄 `abc` 專案 `def` （目錄）、`def/ghi` 和 `jkl`，則程式碼會：

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

會以 `path("abc/def/ghi")` 和 `path("abc/jkl")` 的引數呼叫造訪。 您可以透過兩種方式來限定目錄子樹的排序：

1. 只有當您使用 `directory_options` 引數（其值為 `directory_options::follow_directory_symlink`）來建立 `recursive_directory_iterator` 時，才會掃描目錄符號。

1. 如果您呼叫 `disable_recursion_pending` 則在增量期間遇到的後續目錄將不會以遞迴方式掃描。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|建構 `recursive_directory_iterator`。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[豐富](#depth)|傳回 `mystack.size() - 1`，因此 `pval` 的深度為零。|
|[disable_recursion_pending](#disable_recursion_pending)|會將**true**儲存在 `no_push` 中。|
|[連續](#increment)|依序前進到下一個檔案名。|
|[options](#options)|傳回 `myoptions`。|
|[pop](#pop)|傳回下一個物件。|
|[recursion_pending](#recursion_pending)|傳回 `!no_push`。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](#op_neq)|傳回 `!(*this == right)`。|
|[operator=](#op_as)|預設成員指派運算子會如預期般運作。|
|[operator==](#op_eq)|只有當 `*this` 和*許可權*都是序列結尾反覆運算器，或兩者都不是序列結尾反覆運算器時，才會傳回**true** 。|
|[operator*](#op_multiply)|傳回 `myentry`。|
|[operator->](#op_cast)|傳回 `&**this`。|
|[operator++](#op_increment)|遞增 `recursive_directory_iterator`。|

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：** std::tr2::sys

## <a name="depth"></a>recursive_directory_iterator：:d epth

傳回 `mystack.size() - 1`，因此 `pval` 的深度為零。

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a>recursive_directory_iterator：:d isable_recursion_pending

會將**true**儲存在 `no_push` 中。

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a>recursive_directory_iterator：：遞增值

依序前進到下一個檔案名。

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>參數

*ec* \
指定的錯誤碼。

### <a name="remarks"></a>備註

此函式會嘗試前進到巢狀序列中的下一個檔案名稱。 如果成功，它會將該檔案名儲存在 `myentry`;否則，它會產生結束序列反覆運算器。

## <a name="op_neq"></a>recursive_directory_iterator：： operator！ =

傳回 `!(*this == right)`。

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*right* \
要比較的[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="op_as"></a>recursive_directory_iterator：： operator =

預設成員指派運算子會如預期般運作。

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>參數

*recursive_directory_iterator* \
要複製到 `recursive_directory_iterator` 中的[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="op_eq"></a>recursive_directory_iterator：： operator = =

只有當 `*this` 和*許可權*都是序列結尾反覆運算器，或兩者都不是序列結尾反覆運算器時，才會傳回**true** 。

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*right* \
要比較的[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="op_multiply"></a>recursive_directory_iterator：： operator *

傳回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a>recursive_directory_iterator：： operator->

傳回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>recursive_directory_iterator：： operator + +

遞增 `recursive_directory_iterator`。

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>參數

*int* \
指定的增量。

### <a name="remarks"></a>備註

第一個成員函式會呼叫 `increment()`，然後傳回 `*this`。 第二個成員函式會建立物件的複本、呼叫 `increment()`，然後傳回復本。

## <a name="options"></a>recursive_directory_iterator：： options

傳回 `myoptions`。

```cpp
directory_options options() const;
```

## <a name="pop"></a>recursive_directory_iterator：:p op

傳回下一個物件。

```cpp
void pop();
```

### <a name="remarks"></a>備註

如果 `depth() == 0` 物件會成為序列結尾反覆運算器。 否則，此成員函式會終止掃描目前 (最深) 的目錄，並在次深的目錄繼續掃描。

## <a name="recursion_pending"></a>recursive_directory_iterator::recursion_pending

傳回 `!no_push`。

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a>recursive_directory_iterator::recursive_directory_iterator

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

*pval* \
指定的路徑。

*error_code* \
指定的錯誤碼。

選擇 \
指定的目錄選項。

*recursive_directory_iterator* \
要從中複製所建構之 `recursive_directory_iterator` 的 `recursive_directory_iterator`。

### <a name="remarks"></a>備註

第一個建構函式會產生序列結尾迭代器。 第二個和第三個函式會將**false**儲存在 `myoptions` 中的 `no_push` 和 `directory_options::none`，然後嘗試以目錄的形式開啟和讀取*pval* 。 如果成功，則會初始化 `mystack`，並 `myentry` 指定嵌套順序中的第一個非目錄檔案名;否則，它們會產生結束序列反覆運算器。

第四個和第五個函式的行為與第二個和第三個相同，不同之處在于它們會先將*選擇儲存 `myoptions`* 。 預設建構函式會如預期般運作。

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)
