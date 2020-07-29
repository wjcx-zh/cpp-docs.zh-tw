---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: b28f4554610d37b881494748f75499f46cd9e8d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230229"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

包含 C 標準程式庫標頭 \<assert.h> ，並將相關名稱新增至 `std` 命名空間。 包含此標頭可確保在 C 標準程式庫標頭中使用外部連結宣告的名稱會在 `std` 命名空間中宣告。

> [!NOTE]
> \<assert.h>不會定義 **`static_assert`** 宏。

## <a name="syntax"></a>語法

```cpp
#include <cassert>
```

## <a name="macros"></a>巨集

```cpp
#define assert(E)
```

### <a name="remarks"></a>備註

`assert(E)`只有在定義 `assert` 了最後定義或重新定義的 NDEBUG，或*E*轉換成 bool 評估為時，才會是常數 **`true`** 。

## <a name="see-also"></a>另請參閱

[assert 宏、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫總覽](../standard-library/cpp-standard-library-overview.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
