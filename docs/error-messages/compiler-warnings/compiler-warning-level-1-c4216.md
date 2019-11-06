---
title: 編譯器警告（層級1） C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 69559348a27151a22b11cae8d821110d923cd803
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627330"
---
# <a name="compiler-warning-level-1-c4216"></a>編譯器警告（層級1） C4216

使用非標準的擴充： float long

預設的 Microsoft extensions （/Ze）會將**float long**視為**double**。 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）則不會。 使用**double**來維護相容性。 下列範例會產生 C4216：

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```