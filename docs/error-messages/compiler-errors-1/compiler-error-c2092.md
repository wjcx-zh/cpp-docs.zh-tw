---
title: 編譯器錯誤 C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: d3d0b0e62fbc5f8ad90b3fee5fe39c6bdaba7c2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644609"
---
# <a name="compiler-error-c2092"></a>編譯器錯誤 C2092

'array name' 陣列元素類型不可為函式

不允許函式的陣列。 使用函式的指標陣列。

## <a name="example"></a>範例

下列範例會產生 C2092:

```
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

## <a name="example"></a>範例

可能的解決方式：

```
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```