---
title: recursive_directory_iterator 類別
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 52e6f738aa226dba26bae0cf6e97cd18d107d677
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593333"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator 類別

描述輸入迭代器可循序遍訪目錄中的檔案名稱可能遞減至子目錄以遞迴方式。 迭代器`X`，運算式`*X`評估為類別的物件`directory_entry`包裝檔案名稱和任何已知的狀態項目。

如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>備註

此範本類別會儲存：

1. 型別的物件`stack<pair<directory_iterator, path>>`，稱為`mystack`這裡基於有展銷的目的，用來表示要排序的目錄的巢狀

1. 型別的物件`directory_entry`稱為`myentry`這裡，表示目錄序列中的目前檔案名稱

1. 型別的物件**bool**稱為`no_push`這裡，這會記錄是否已停用遞迴下降到子目錄

1. 型別的物件`directory_options`，稱為`myoptions`這裡，這會記錄建立建構的選項

類型的預設建構物件`recursive_directory_entry`具有結束序列迭代器在`mystack.top().first`並代表結束序列迭代器。 例如，假設目錄`abc`項目的`def`（目錄） `def/ghi`，和`jkl`，程式碼：

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

使用引數將會呼叫 visit`path("abc/def/ghi")`和`path("abc/jkl")`。 您可以限定子樹狀目錄中兩種方式可以透過排序：

1. 只有當您建構，就會掃描目錄符號連結`recursive_directory_iterator`具有`directory_options`引數其值是`directory_options::follow_directory_symlink`。

1. 如果您呼叫`disable_recursion_pending`遞增期間遇到的後續目錄就不會以遞迴方式掃描。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|建構 `recursive_directory_iterator`。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[深度](#depth)|傳回`mystack.size() - 1`，因此`pval`的深度為零。|
|[disable_recursion_pending](#disable_recursion_pending)|存放區**真**在`no_push`。|
|[遞增值](#increment)|前移到序列中下一步 的檔案名稱。|
|[options](#options)|傳回 `myoptions`。|
|[pop](#pop)|傳回下一個物件。|
|[recursion_pending](#recursion_pending)|傳回 `!no_push`。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](#op_neq)|傳回 `!(*this == right)`。|
|[operator=](#op_as)|預設成員指派運算子會如預期般運作。|
|[operator==](#op_eq)|傳回 **，則為 true**只有兩個`*this`及*右*結束序列迭代器，或兩者都不結束-的--迭代器。|
|[operator*](#op_multiply)|傳回 `myentry`。|
|[operator->](#op_cast)|傳回 `&**this`。|
|[operator++](#op_increment)|遞增`recursive_directory_iterator`。|

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：** std::tr2::sys

## <a name="depth"></a> recursive_directory_iterator:: depth

傳回`mystack.size() - 1`，因此`pval`的深度為零。

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a> recursive_directory_iterator:: disable_recursion_pending

存放區**真**在`no_push`。

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a> recursive_directory_iterator:: increment

前移到序列中下一步 的檔案名稱。

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>參數

*ec*<br/>
指定的錯誤碼。

### <a name="remarks"></a>備註

此函式會嘗試前進到巢狀序列中的下一個檔案名稱。 如果成功，它會儲存在該檔案名稱`myentry`; 否則會產生結束序列迭代器。

## <a name="op_neq"></a> recursive_directory_iterator:: operator ！ =

傳回 `!(*this == right)`。

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)進行比較。

## <a name="op_as"></a> recursive_directory_iterator:: operator =

預設成員指派運算子會如預期般運作。

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>參數

*recursive_directory_iterator*<br/>
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)複製到`recursive_directory_iterator`。

## <a name="op_eq"></a> recursive_directory_iterator:: operator = =

傳回 **，則為 true**只有兩個`*this`及*右*結束序列迭代器，或兩者都不結束-的--迭代器。

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)進行比較。

## <a name="op_multiply"></a> recursive_directory_iterator:: operator *

傳回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> recursive_directory_iterator:: operator->

傳回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> recursive_directory_iterator:: operator + +

遞增`recursive_directory_iterator`。

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>參數

*int*<br/>
指定的遞增值。

### <a name="remarks"></a>備註

第一個成員函式會呼叫`increment()`，然後傳回`*this`。 第二個成員函式會建立一份物件，呼叫`increment()`，然後傳回複本。

## <a name="options"></a> recursive_directory_iterator:: options

傳回 `myoptions`。

```cpp
directory_options options() const;
```

## <a name="pop"></a> recursive_directory_iterator:: pop

傳回下一個物件。

```cpp
void pop();
```

### <a name="remarks"></a>備註

如果`depth() == 0`物件會變成結束序列迭代器。 否則，此成員函式會終止掃描目前 (最深) 的目錄，並在次深的目錄繼續掃描。

## <a name="recursion_pending"></a> recursive_directory_iterator:: recursion_pending

傳回 `!no_push`。

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a> recursive_directory_iterator:: recursive_directory_iterator

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

*pval*<br/>
指定的路徑。

*error_code*<br/>
指定的錯誤碼。

*選擇*<br/>
指定的目錄的選項。

*recursive_directory_iterator*<br/>
要從中複製所建構之 `recursive_directory_iterator` 的 `recursive_directory_iterator`。

### <a name="remarks"></a>備註

第一個建構函式會產生序列結尾迭代器。 第二個和第三個建構函式存放區**false**中`no_push`並`directory_options::none`中`myoptions`，然後嘗試開啟並讀取*pval*做為目錄。 如果成功，則會初始化`mystack`和`myentry`指定第一個非目錄檔案名稱，在巢狀序列中，否則會產生結束序列迭代器。

第四個和第五個建構函式的行為相同做為第二個和第三，不同之處在於其第一次儲存*opts*在`myoptions`。 預設建構函式會如預期般運作。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)<br/>
