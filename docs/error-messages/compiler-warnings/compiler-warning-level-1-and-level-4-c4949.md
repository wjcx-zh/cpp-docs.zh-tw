---
title: 編譯器警告 (層級 1 和層級 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 8050edbd7a653776d046bc7b4155fd43094d9a5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187518"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>編譯器警告 (層級 1 和層級 4) C4949

pragmas 'managed' 和 'unmanaged' 是只在編譯時，才有意義 ' / /clr [: 選項]'

編譯器會忽略[受控](../../preprocessor/managed-unmanaged.md)和非受控 pragma，如果使用未編譯的原始程式碼[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。 這個警告僅供參考。

下列範例會產生 C4949:

```
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

當 **#pragma unmanaged**使用，而沒有 **/clr**，C4949 是層級 4 警告。

下列範例會產生 C4949:

```
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```