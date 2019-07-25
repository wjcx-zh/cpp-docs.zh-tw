---
title: '&lt;csetjmp&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csetjmp>
helpviewer_keywords:
- csetjmp header
ms.assetid: 8f21fddd-5e9b-4219-a848-581cdd3569d9
ms.openlocfilehash: 8f3a1a622776d5dd2ef3d22aaa3436933c5a7137
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452389"
---
# <a name="ltcsetjmpgt"></a>&lt;csetjmp&gt;

包含標準 C 程式庫標頭 \<setjmp.h>，並將關聯名稱加入 `std` 命名空間。

## <a name="syntax"></a>語法

```cpp
#include <csetjmp>

using jmp_buf = see below;
```

## <a name="functions"></a>函式

```cpp
[[noreturn]] void longjmp(jmp_buf env, int val);
```

## <a name="macros"></a>巨集

```cpp
#define setjmp(env)
```

## <a name="remarks"></a>備註

包含此標頭可保證，透過使用 Standard C 程式庫標頭中的外部連結所宣告的名稱會在 `std` 命名空間中宣告。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
