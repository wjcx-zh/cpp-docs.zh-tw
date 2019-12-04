---
title: 編譯器錯誤 C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 24463abcf123fda285356c86e3394d7274f2f6c8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751036"
---
# <a name="compiler-error-c2021"></a>編譯器錯誤 C2021

必須是指數值，而非 'character'

當做浮點常數指數使用的字元不是有效的數位。 請務必使用範圍內的指數。

## <a name="example"></a>範例

下列範例會產生 C2021：

```cpp
// C2021.cpp
float test1=1.175494351E;   // C2021
```

## <a name="example"></a>範例

可能的解決方案：

```cpp
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```
