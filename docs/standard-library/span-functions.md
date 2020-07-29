---
title: '&lt;span &gt; 函數'
ms.date: 05/28/2020
f1_keywords:
- span/std::span::as_bytes
- span/std::as_writable_bytes
helpviewer_keywords:
- std::span [C++], as_writable_bytes
- std::as_bytes [C++]
ms.openlocfilehash: f51c99d2f2a051a07cefcb985fdb46340fefb3ee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217437"
---
# <a name="ltspangt-functions"></a>&lt;span &gt; 函數

\<span>標頭包含下列在**span**物件上操作的非成員函式。

| **非成員函式** | **說明** |
|-|-|
|[as_bytes](#as_bytes) | 取得範圍中元素的物件表示的唯讀視圖。 |
|[as_writable_bytes](#as_writable_bytes) | 取得範圍中元素的物件表示的讀取/寫入視圖。 |

## <a name="as_bytes"></a>`as_bytes`

取得範圍中元素的物件表示的唯讀視圖。

```cpp
template <class T, size_t Extent>
auto as_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>參數

*而已*\
範圍中元素的類型。

*片區*\
範圍中的專案數（如果在編譯時期為已知），否則 `dynamic_extent` 表示在執行時間之前不知道元素的數目。

*今日*\
要取得其原始表示的範圍。

### <a name="return-value"></a>傳回值

， `span<const byte, S>` 指向儲存在範圍中的第一個專案，其中 `S` 是`{reinterpret_cast<const std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = std::as_bytes(mySpan);
}
```

## <a name="as_writable_bytes"></a>`as_writable_bytes`

如果 `T` 不是，則會 **`const`** 取得範圍中元素之原始位元組表示的讀取/寫入視圖。

```cpp
template <class T, size_t Extent>
auto as_writable_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>參數

*而已*\
範圍中元素的類型。

*片區*\
範圍中的專案數（如果在編譯時期為已知），否則 `dynamic_extent` 表示在執行時間之前不知道元素的數目。

*今日*\
要取得其原始表示的範圍。

### <a name="return-value"></a>傳回值

， `span<byte, S>` 指向儲存在範圍中的第一個專案，其中 `S` 是`{reinterpret_cast<std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>範例

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = as_writable_bytes(mySpan);
}
```

## <a name="see-also"></a>另請參閱

[\<span>](span.md)
