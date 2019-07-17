---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 14dda03e835ec411013b2d827bd1ccaa77f8982e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245024"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

包含標準 C 程式庫標頭\<assert.h> >，並將關聯的名稱加入`std`命名空間。 包含此標頭中宣告的宣告 C 標準程式庫標頭中使用外部連結的名稱可確保`std`命名空間。

> [!NOTE]
> \<assert.h> > 未定義`static_assert`巨集。

## <a name="syntax"></a>語法

```cpp
#include <cassert>
```

## <a name="macros"></a>巨集

```cpp
#define assert(E)
```

### <a name="remarks"></a>備註

`assert(E)` 只為常數，如果在定義 NDEBUG 所在`assert`上次定義或重新定義，或*電子*轉換為 bool 評估為 **，則為 true**。

## <a name="see-also"></a>另請參閱

[assert 巨集、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
