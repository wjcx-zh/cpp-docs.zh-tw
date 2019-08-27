---
title: '&lt;climits&gt;'
ms.date: 11/04/2016
f1_keywords:
- <climits>
helpviewer_keywords:
- climits header
ms.assetid: 7ca8a539-aa45-4ac3-86e8-74513be3f07e
ms.openlocfilehash: 6cff0975fb61e30bc96390f345cd67d7b1fbec41
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459342"
---
# <a name="ltclimitsgt"></a>&lt;climits&gt;

包含 C 標準程式庫標\<頭限制 .h > 並將相關名稱新增`std`至命名空間。 包含此標頭可確保在 C 標準程式庫標頭中使用外部連結宣告的名稱會`std`在命名空間中宣告。

## <a name="syntax"></a>語法

```cpp
#include <climits>
```

## <a name="macros"></a>巨集

```cpp
#define CHAR_BIT
#define SCHAR_MIN
#define SCHAR_MAX
#define UCHAR_MAX
#define CHAR_MIN
#define CHAR_MAX
#define MB_LEN_MAX
#define SHRT_MIN
#define SHRT_MAX
#define USHRT_MAX
#define INT_MIN
#define INT_MAX
#define UINT_MAX
#define LONG_MIN
#define LONG_MAX
#define ULONG_MAX
#define LLONG_MIN
#define LLONG_MAX
#define ULLONG_MAX
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
