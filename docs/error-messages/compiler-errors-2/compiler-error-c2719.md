---
title: 編譯器錯誤 C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: d635601fbf8b36218fb47c09444f3f5d023c823e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383083"
---
# <a name="compiler-error-c2719"></a>編譯器錯誤 C2719

'parameter'：具有 __declspec(align('#')) 的型式參數不會對齊

[對齊](../../cpp/align-cpp.md)`__declspec`函式參數，不允許修飾詞。 函式參數對齊可藉由所使用的呼叫慣例來控制。 如需詳細資訊，請參閱 <<c0> [ 呼叫慣例](../../cpp/calling-conventions.md)。

下列範例會產生 C2719，並說明如何加以修正：

```
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```