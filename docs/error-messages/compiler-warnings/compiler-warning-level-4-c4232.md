---
title: 編譯器警告 (層級 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: 9d328b1b5e4c3875f29b48eab77cd6f6d49d447f
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541884"
---
# <a name="compiler-warning-level-4-c4232"></a>編譯器警告 (層級 4) C4232

使用非標準的擴充： ' identifier '： dllimport ' dllimport ' 的位址不是靜態的，無法保證身分識別

在 Microsoft extensions （/Ze）底下，您可以將非靜態值指定為使用**dllimport**修飾詞宣告之函式的位址。 在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下，這會造成錯誤。

下列範例會產生 C4232：

```c
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```