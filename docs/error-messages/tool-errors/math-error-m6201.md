---
title: 運算錯誤 M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 0b1cd0d3fcd86a2174b19da41176dd97f547a295
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193702"
---
# <a name="math-error-m6201"></a>運算錯誤 M6201

' function '： _DOMAIN 錯誤

給定函式的引數超出該函數的合法輸入值定義域。

## <a name="example"></a>範例

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

此錯誤會使用函式名稱、其引數和錯誤類型來呼叫 `_matherr` 函式。 您可以重寫 `_matherr` 函式，以自訂特定執行時間浮點運算錯誤的處理。
