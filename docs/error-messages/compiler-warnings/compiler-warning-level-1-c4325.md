---
title: 編譯器警告 (層級 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 551680bc1d24097200a1e641bc4238f883ad94dd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230697"
---
# <a name="compiler-warning-level-1-c4325"></a>編譯器警告 (層級 1) C4325

> 已忽略標準區段 '*section*' 的屬性

## <a name="remarks"></a>備註

您不能變更標準區段的屬性。 例如：

```cpp
#pragma section(".sdata", long)
```

這會覆寫 `.sdata` 使用 **`short`** 資料類型與資料類型的標準區段 **`long`** 。

您可能不會變更其屬性的標準區段包括、

- 。資料

- .sdata

- . bss

- .sbss

- .text

- const

- .sconst

- . .rdata

- .srdata

稍後可能會新增其他區段。

## <a name="see-also"></a>另請參閱

[截面](../../preprocessor/section.md)
