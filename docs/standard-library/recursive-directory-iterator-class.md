---
title: recursive_directory_iterator 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
dev_langs:
- C++
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3e1ef6dab66e0414ecace7b6e51b31eef632d06
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator 類別

描述可循序遍訪目錄中的檔案名稱的輸入迭代器，可能會以遞迴方式下降到子目錄。 對於迭代器 X，運算式 *X 會評估為 directory_entry 類別的物件，該物件會包裝檔案名稱及其狀態的任何已知項目。

如需詳細資訊與程式碼範例，請參閱[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>語法

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>備註

此範本類別會儲存：

1. stack<pair\<directory_iterator, path>> 類型的物件，在此稱為 mystack 以用於說明，該物件代表要循序遍訪之目錄的巢狀結構

1. directory_entry 類型的物件，在此稱為 myentry，該物件代表目錄序列中的目前檔案名稱。

1. bool 類型的物件，在此稱為 no_push，該物件會記錄是否已停用遞迴下降到子目錄

1. directory_options 類型的物件，在此稱為 myoptions，該物件會記錄建構時所建立的選項

recursive_directory_entry 類型的預設建構物件在 mystack.top().first 具有結束序列 (end-of-sequence) 迭代器，並代表結束序列迭代器。例如，假設目錄 abc 具有項目 def (目錄)、def/ghi 和 jkl，則程式碼為：

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

將會呼叫 visit 並提供引數 `path("abc/def/ghi") and path("abc/jkl").`。您可以透過兩種方式，來限定子樹狀目錄中的循序遍訪：

1. 只有在您使用其值為 directory_options::follow_directory_symlink 之 directory_options 引數來建構 recursive_directory_iterator 時，才會掃描目錄符號連結。

1. 如果您呼叫 disable_recursion_pending，則不會以遞迴方式掃描在遞增期間遇到的後續目錄。

## <a name="recursivedirectoryiteratordepth"></a>recursive_directory_iterator::depth

```cpp
int depth() const;
```

傳回 mystack.size() - 1，因此 pval 的深度為零。

## <a name="recursivedirectoryiteratordisablerecursionpending"></a>recursive_directory_iterator::disable_recursion_pending

```cpp
void disable_recursion_pending();
```

此成員函式會在 no_push 中儲存 true。

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator!=

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

此成員運算子會傳回 !(*this == right)。

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator=

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

預設成員指派運算子會如預期般運作。

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator==

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

只有在 *this 和 right 都是或都不是結束序列迭代器時，此成員運算子才會傳回 true。

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator*

```cpp
const directory_entry& operator*() const;
```

此成員運算子會傳回 myentry。

## <a name="recursivedirectoryiteratoroperator-"></a>recursive_directory_iterator::operator->

```cpp
const directory_entry * operator->() const;
```

傳回 &**this。

## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator++

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

第一個成員函式會呼叫 increment()，然後傳回 *this。 第二個成員函式會複製物件、呼叫 increment()，然後傳回複本。

## <a name="recursivedirectoryiteratoroptions"></a>recursive_directory_iterator::options

```cpp
directory_options options() const;
```

傳回 myoptions。

## <a name="recursivedirectoryiteratorpop"></a>recursive_directory_iterator::pop

```cpp
void pop();
```

如果 depth() == 0，則物件會變成結束序列迭代器。 否則，此成員函式會終止掃描目前 (最深) 的目錄，並在次深的目錄繼續掃描。

## <a name="recursivedirectoryiteratorrecursionpending"></a>recursive_directory_iterator::recursion_pending

```cpp
bool recursion_pending() const;
```

傳回 !no_push。

## <a name="recursivedirectoryiteratorrecursivedirectoryiterator"></a>recursive_directory_iterator::recursive_directory_iterator

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

第一個建構函式會產生結束序列迭代器。 第二個和第三個建構函式會在 no_push 和 myoptions 的 directory_options::none 中儲存 false，然後嘗試以目錄形式開啟並讀取 pval。 如果成功，則會初始化 mystack 和 myentry 以指定巢狀序列中的第一個非目錄檔案名稱，否則會產生結束序列迭代器。

第四個和第五個建構函式的行為，與第二個和第三建構函式的行為相同，不過會先在 myoptions 中儲存 opts。 預設建構函式會如預期般運作。

## <a name="recursivedirectoryiteratorincrement"></a>recursive_directory_iterator::increment

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

此函式會嘗試前進到巢狀序列中的下一個檔案名稱。 如果成功，則會在 myentry 中儲存該檔案名稱，否則會產生序列結尾迭代器。

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：** std::tr2::sys

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)<br/>
