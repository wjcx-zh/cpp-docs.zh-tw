---
title: 編譯器警告 (層級 1 和層級 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 7ce8b3242def187e4b8b442f403f92f013a9ca6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164777"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>編譯器警告 (層級 1 和層級 4) C4949

pragma ' managed ' 和 ' 非受控 ' 只有在以 '/clr [： option] ' 編譯時才有意義

如果原始程式碼不是使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯，編譯器會忽略[managed](../../preprocessor/managed-unmanaged.md)和非受控 pragma。 這個警告僅供參考。

下列範例會產生 C4949：

```cpp
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

若未使用 **/clr** **#pragma 非受控**，則 C4949 會是層級4警告。

下列範例會產生 C4949：

```cpp
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```
