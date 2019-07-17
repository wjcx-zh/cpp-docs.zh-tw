---
title: '&lt;cstdarg&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdarg>
helpviewer_keywords:
- cstdarg header
ms.assetid: 639b4ef7-8408-4640-9343-41631f0ab663
ms.openlocfilehash: f8d2d3b886cfa46905e8f17f1e13b51881b80191
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244490"
---
# <a name="ltcstdarggt"></a>&lt;cstdarg&gt;

包含標準 C 程式庫標頭\<stdarg.h> >，並將關聯的名稱加入`std`命名空間。 包含此標頭中宣告的宣告 C 標準程式庫標頭中使用外部連結的名稱可確保`std`命名空間。

## <a name="syntax"></a>語法

```cpp
#include <cstdarg>
```

## <a name="namespace-and-macros"></a>命名空間和巨集

```cpp
namespace std {
    using va_list = see below;
}

#define va_arg(V, P)
#define va_copy(VDST, VSRC)
#define va_end(V)
#define va_start(V, P)
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
