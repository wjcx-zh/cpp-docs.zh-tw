---
title: '&lt;csetjmp&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csetjmp>
helpviewer_keywords:
- csetjmp header
ms.assetid: 8f21fddd-5e9b-4219-a848-581cdd3569d9
ms.openlocfilehash: 3eba0b4521c0abf414de1416f02039a67c896644
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244509"
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

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
