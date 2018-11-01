---
title: 編譯器錯誤 C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 6492dfffbb5a2f80ea543d4248c0f77759c0a521
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513997"
---
# <a name="compiler-error-c2021"></a>編譯器錯誤 C2021

必須是指數值，而非 'character'

浮點常數的指數所用的字元不是有效的數字。 請務必使用在範圍內的指數。

## <a name="example"></a>範例

下列範例會產生 C2021:

```
// C2021.cpp
float test1=1.175494351E;   // C2021
```

## <a name="example"></a>範例

可能的解決方式：

```
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```