---
title: directory_iterator 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: 36cbf9e8d4ebdf62cbbfdc5a37ca1c49d7106a42
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105199"
---
# <a name="directoryiterator-class"></a>directory_iterator 類別

描述可循序遍訪目錄中的檔案名稱的輸入迭代器。 對於迭代器 X，運算式 *X 會評估為 directory_entry 類別的物件，該物件會包裝檔案名稱及其狀態的任何已知項目。

此類別會儲存類型路徑，呼叫的物件`mydir`這裡基於有展銷的目的，用來表示要排序之目錄的名稱和呼叫物件的類型 directory_entry`myentry`這裡，表示目前的檔案名稱中目錄序列中。 預設建構物件的類型 directory_entry 具有空白`mydir`路徑名稱，而代表結束序列迭代器。

例如，假設目錄 abc 有項目 def 和 ghi，程式碼：

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

會呼叫`visit`引數 path 與 visit。

如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class directory_iterator;
```

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[directory_iterator](#directory_iterator)|建構輸入迭代器可循序遍訪目錄中的檔案名稱。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[遞增值](#increment)|此函式會嘗試前進到目錄中的下一個檔案名稱。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](#op_neq)|傳回 `!(*this == right)`。|
|[operator=](#op_as)|預設成員指派運算子會如預期般運作。|
|[operator==](#op_eq)|傳回 **，則為 true**只有兩個`*this`及*右*結束序列迭代器，或兩者都不結束-的--迭代器。|
|[operator*](#op_star)|傳回 `myentry`。|
|[operator->](#op_cast)|傳回 `&**this`。|
|[operator++](#op_increment)|呼叫`increment()`，然後傳回`*this`，或複製的物件，呼叫`increment()`，然後傳回複本。|

## <a name="requirements"></a>需求

**標頭：**\<experimental/filesystem>

**命名空間：** std::experimental::filesystem

## <a name="directory_iterator"></a> directory_iterator:: directory_iterator

第一個建構函式會產生序列結尾迭代器。 第二個和第三個建構函式存放區*pval*中`mydir`，然後嘗試開啟並讀取`mydir`做為目錄。 如果成功，其儲存的第一個檔名的目錄中`myentry`; 否則會產生結束序列迭代器。

預設建構函式會如預期般運作。

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>參數

*pval*<br/>
儲存的檔案名稱路徑。

*ec*<br/>
狀態錯誤程式碼。 

*directory_iterator*<br/>
預存的物件。

## <a name="increment"></a> directory_iterator:: increment

此函式會嘗試前進到目錄中的下一個檔案名稱。 如果成功，它會儲存在該檔案名稱`myentry`; 否則會產生結束序列迭代器。

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a> directory_iterator:: operator ！ =

此成員運算子會傳回 `!(*this == right)`。

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
[Directory_iterator](../standard-library/directory-iterator-class.md)比較`directory_iterator`。

## <a name="op_as"></a> directory_iterator:: operator =

預設成員指派運算子會如預期般運作。

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>參數

*right*<br/>
[Directory_iterator](../standard-library/directory-iterator-class.md)複製到`directory_iterator`。

## <a name="op_eq"></a> directory_iterator:: operator = =

成員運算子會傳回 **，則為 true**只有兩個`*this`及*右*結束序列迭代器，或兩者都不結束-的--迭代器。

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
[Directory_iterator](../standard-library/directory-iterator-class.md)比較`directory_iterator`。

## <a name="op_star"></a> directory_iterator:: operator *

此成員運算子會傳回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> directory_iterator:: operator->

成員函式會傳回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> directory_iterator:: operator + +

第一個成員函式會呼叫`increment()`，然後傳回`*this`。 第二個成員函式會建立一份物件，呼叫`increment()`，然後傳回複本。

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>參數

*int*<br/>
增量數目。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)<br/>
