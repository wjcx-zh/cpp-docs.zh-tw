---
title: recursive_directory_iterator 類別
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 98eaf2494a3bc17c0f9d11683fc67fed433ba3a5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451699"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator 類別

描述輸入反覆運算器, 其會將目錄中的檔案名進行序列處理, 可能會以遞迴方式遞減為子目錄。 若為 iterator `X`, 運算式`*X`會評估為類別`directory_entry`的物件, 其會包裝檔案名和任何已知的狀態。

如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>備註

此範本類別會儲存：

1. 類型`stack<pair<directory_iterator, path>>`的物件, 針對展示`mystack`的目的在此呼叫, 這代表要排序的目錄的嵌套

1. 在這裡呼叫`myentry`類型`directory_entry`的物件, 其代表目錄序列中的目前檔案名

1. **bool**類型的物件, 在此`no_push`呼叫會記錄是否已停用遞迴下降到子目錄中

1. 類型`directory_options`的物件, 在此`myoptions`稱為, 其會記錄在結構中建立的選項

類型`recursive_directory_entry`的預設結構化物件具有在`mystack.top().first`的結束序列反覆運算器, 代表序列結尾反覆運算器。 例如`abc` , 假設目錄包含專案`def` (目錄)、 `def/ghi`和`jkl`, 則程式碼會:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

會以引數`path("abc/def/ghi")`和`path("abc/jkl")`呼叫造訪。 您可以透過兩種方式來限定目錄子樹的排序:

1. 只有當您`recursive_directory_iterator` `directory_options`使用值為`directory_options::follow_directory_symlink`的引數來建立時, 才會掃描目錄符號。

1. 如果您呼叫`disable_recursion_pending` , 則在增量期間遇到的後續目錄將不會以遞迴方式掃描。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|建構 `recursive_directory_iterator`。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[depth](#depth)|會傳回`pval` , 因此深度為零。 `mystack.size() - 1`|
|[disable_recursion_pending](#disable_recursion_pending)|將**true**儲存`no_push`在中。|
|[increment](#increment)|依序前進到下一個檔案名。|
|[options](#options)|傳回 `myoptions`。|
|[pop](#pop)|傳回下一個物件。|
|[recursion_pending](#recursion_pending)|傳回 `!no_push`。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](#op_neq)|傳回 `!(*this == right)`。|
|[operator=](#op_as)|預設成員指派運算子會如預期般運作。|
|[operator==](#op_eq)|只有當`*this`和*許可權*都是序列結尾反覆運算器, 或兩者都不是序列結尾反覆運算器時, 才會傳回 true。|
|[operator*](#op_multiply)|傳回 `myentry`。|
|[operator->](#op_cast)|傳回 `&**this`。|
|[operator++](#op_increment)|`recursive_directory_iterator`遞增。|

## <a name="requirements"></a>需求

**標頭:** \<filesystem >

**命名空間：** std::tr2::sys

## <a name="depth"></a>recursive_directory_iterator::d epth

會傳回`pval` , 因此深度為零。 `mystack.size() - 1`

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a>recursive_directory_iterator::d isable_recursion_pending

將**true**儲存`no_push`在中。

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a>recursive_directory_iterator:: 遞增值

依序前進到下一個檔案名。

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>參數

*歐洲*\
指定的錯誤碼。

### <a name="remarks"></a>備註

此函式會嘗試前進到巢狀序列中的下一個檔案名稱。 如果成功, 它會在中`myentry`儲存該檔案名, 否則會產生序列結尾反覆運算器。

## <a name="op_neq"></a>recursive_directory_iterator:: operator! =

傳回 `!(*this == right)`。

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*再*\
要比較的[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="op_as"></a>recursive_directory_iterator:: operator =

預設成員指派運算子會如預期般運作。

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>參數

*recursive_directory_iterator*\
要[](../standard-library/recursive-directory-iterator-class.md)複製到`recursive_directory_iterator`中的 recursive_directory_iterator。

## <a name="op_eq"></a>recursive_directory_iterator:: operator = =

只有當`*this`和*許可權*都是序列結尾反覆運算器, 或兩者都不是序列結尾反覆運算器時, 才會傳回 true。

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*再*\
要比較的[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="op_multiply"></a>recursive_directory_iterator:: operator *

傳回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a>recursive_directory_iterator:: operator->

傳回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>recursive_directory_iterator:: operator + +

`recursive_directory_iterator`遞增。

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>參數

*int*\
指定的增量。

### <a name="remarks"></a>備註

第一個成員函式`increment()`會呼叫, `*this`然後傳回。 第二個成員函式會建立物件的複本、 `increment()`呼叫, 然後傳回復本。

## <a name="options"></a>recursive_directory_iterator:: options

傳回 `myoptions`。

```cpp
directory_options options() const;
```

## <a name="pop"></a>recursive_directory_iterator::p op

傳回下一個物件。

```cpp
void pop();
```

### <a name="remarks"></a>備註

如果`depth() == 0`物件成為序列的結尾反覆運算器, 則為。 否則，此成員函式會終止掃描目前 (最深) 的目錄，並在次深的目錄繼續掃描。

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

*pval*\
指定的路徑。

*error_code*\
指定的錯誤碼。

*opts*\
指定的目錄選項。

*recursive_directory_iterator*\
要從中複製所建構之 `recursive_directory_iterator` 的 `recursive_directory_iterator`。

### <a name="remarks"></a>備註

第一個建構函式會產生序列結尾迭代器。 第二個和第三個函`no_push`式`directory_options::none`會`myoptions`在和中儲存**false** , 然後嘗試以目錄的形式開啟和讀取*pval* 。 如果成功, 則會`mystack`初始化`myentry`並指定嵌套順序中的第一個非目錄檔案名, 否則會產生結束序列反覆運算器。

第四個和第五個函式的行為與第二個和第三個相同, `myoptions`不同之處在于它們會先儲存選擇。 預設建構函式會如預期般運作。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)
