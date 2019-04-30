---
title: 運算錯誤 M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 6d3f107de7e45653374036ecafaa864cb3eff5b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393242"
---
# <a name="math-error-m6201"></a>運算錯誤 M6201

'function': 錯誤 （_d）

指定的函式的引數超出合法的輸入值，該函式的網域。

## <a name="example"></a>範例

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

這個錯誤呼叫`_matherr`函式名稱、 其引數，與錯誤類型的函式。 您可以重新撰寫`_matherr`函式來自訂特定執行階段浮點數學錯誤的處理。