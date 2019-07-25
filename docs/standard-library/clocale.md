---
title: '&lt;clocale&gt;'
ms.date: 11/04/2016
f1_keywords:
- <clocale>
helpviewer_keywords:
- clocale header
ms.assetid: 5bde3e01-cf67-4f1f-a383-447ec814d00e
ms.openlocfilehash: 60d15795328de567a8ba626f5344b2fb08e57aa7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459343"
---
# <a name="ltclocalegt"></a>&lt;clocale&gt;

包含標準 C 程式庫標頭 \<locale.h>，並將相關名稱新增至 `std` 命名空間。

## <a name="requirements"></a>需求

**標頭:** \<clocale >

**命名空間：** std

## <a name="remarks"></a>備註

包含此標頭可保證，透過使用 Standard C 程式庫標頭中的外部連結所宣告的名稱會在 `std` 命名空間中宣告。

## <a name="constants"></a>常數

```cpp
#define NULL see below
#define LC_ALL see below
#define LC_COLLATE see below
#define LC_CTYPE see below
#define LC_MONETARY see below
#define LC_NUMERIC see below
#define LC_TIME see below
```

## <a name="structures"></a>結構

```cpp
struct lconv;
```

## <a name="functions"></a>函式

```cpp
char* setlocale(int category, const char* locale);
lconv* localeconv();
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
