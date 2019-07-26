---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 58ebd91fb4fa32cf31d2c49429d0445b92fe0c82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449914"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

包含 C 標準程式庫標\<頭 assert. h >, 並將相關聯的`std`名稱加入至命名空間。 包含此標頭可確保在 C 標準程式庫標頭中使用外部連結宣告的名稱會`std`在命名空間中宣告。

> [!NOTE]
> \<> 不會定義`static_assert`宏。

## <a name="syntax"></a>語法

```cpp
#include <cassert>
```

## <a name="macros"></a>巨集

```cpp
#define assert(E)
```

### <a name="remarks"></a>備註

`assert(E)`只有在定義了最後定義或重新定義`assert`的 NDEBUG, 或*E*轉換成 bool 評估為**true**時, 才會是常數。

## <a name="see-also"></a>另請參閱

[assert 巨集、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
