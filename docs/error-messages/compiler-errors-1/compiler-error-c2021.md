---
title: 編譯器錯誤 C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 97d1776bb3b29b3691ae31bb060410a83d581e2d
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743291"
---
# <a name="compiler-error-c2021"></a>編譯器錯誤 C2021

必須是指數值，而非 'character'

當做浮點數常數的指數使用的字元不是有效的數位。 請務必使用範圍中的指數。

## <a name="examples"></a>範例

下列範例會產生 C2021：

```cpp
// C2021.cpp
float test1=1.175494351E;   // C2021
```

可能的解決方式：

```cpp
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```
