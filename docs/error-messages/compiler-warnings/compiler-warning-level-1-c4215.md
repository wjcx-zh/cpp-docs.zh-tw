---
title: 編譯器警告 (層級 1) C4215
ms.date: 11/04/2016
f1_keywords:
- C4215
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
ms.openlocfilehash: a45cd6cf86eb8ab1edb33ad5e0df8374972c425e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386482"
---
# <a name="compiler-warning-level-1-c4215"></a>編譯器警告 (層級 1) C4215

使用非標準擴充： long float

預設的 Microsoft 擴充功能 (/Ze) 視為**long float**作為**double**。 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 則否。 使用**double**維護相容性。

下列範例會產生 C4215:

```
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```