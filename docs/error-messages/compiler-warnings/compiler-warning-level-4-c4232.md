---
title: 編譯器警告 (層級 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: 6081acc4a64394c9122650da8b7f4147f724e5de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219920"
---
# <a name="compiler-warning-level-4-c4232"></a>編譯器警告 (層級 4) C4232

使用非標準的擴充： ' identifier '： dllimport ' dllimport ' 的位址不是靜態的，無法保證身分識別

在 Microsoft extensions （/Ze）底下，您可以提供非靜態值做為使用修飾詞所宣告之函式的位址 **`dllimport`** 。 在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下，這會造成錯誤。

下列範例會產生 C4232：

```c
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```
