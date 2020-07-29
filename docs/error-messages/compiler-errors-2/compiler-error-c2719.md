---
title: 編譯器錯誤 C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: a0a993069a0bd232154cf6c1b365c0828d9bede8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220245"
---
# <a name="compiler-error-c2719"></a>編譯器錯誤 C2719

'parameter'：具有 __declspec(align('#')) 的型式參數不會對齊

[align](../../cpp/align-cpp.md) **`__declspec`** 函數參數上不允許有 align 修飾詞。 函式參數對齊可藉由所使用的呼叫慣例來控制。 如需詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。

下列範例會產生 C2719，並說明如何加以修正：

```cpp
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```
