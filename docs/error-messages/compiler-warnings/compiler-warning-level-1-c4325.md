---
title: 編譯器警告 (層級 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 293cbbcfe134f6cb4f5e1bf924be7c03fa278833
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408533"
---
# <a name="compiler-warning-level-1-c4325"></a>編譯器警告 (層級 1) C4325

> 忽略標準區段 '*一節*' 略過

## <a name="remarks"></a>備註

您可能不會變更標準區段的屬性。 例如：

```cpp
#pragma section(".sdata", long)
```

這會覆寫`.sdata`它會使用標準區段**簡短**資料型別有**長**資料型別。

您無法變更其屬性包含，標準的區段

- .data

- .sdata

- .bss

- .sbss

- .text

- .const

- .sconst

- .rdata

- .srdata

稍後可能會加入其他區段。

## <a name="see-also"></a>另請參閱

[section](../../preprocessor/section.md)