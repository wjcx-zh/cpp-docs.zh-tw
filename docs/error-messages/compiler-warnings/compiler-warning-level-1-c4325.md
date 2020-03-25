---
title: 編譯器警告 (層級 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: e0a13761b0657d054065358994638779817dad6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163020"
---
# <a name="compiler-warning-level-1-c4325"></a>編譯器警告 (層級 1) C4325

> 已忽略標準區段 '*section*' 的屬性

## <a name="remarks"></a>備註

您不能變更標準區段的屬性。 例如：

```cpp
#pragma section(".sdata", long)
```

這會覆寫使用**long**資料類型之**short**資料類型的 `.sdata` standard 區段。

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

[section](../../preprocessor/section.md)
