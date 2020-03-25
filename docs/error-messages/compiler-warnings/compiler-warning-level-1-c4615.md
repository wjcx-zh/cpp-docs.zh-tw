---
title: 編譯器警告 (層級 1) C4615
ms.date: 11/04/2016
f1_keywords:
- C4615
helpviewer_keywords:
- C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
ms.openlocfilehash: 5d8c5ae1214b3e823bb3754e3b200a430026f1b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185915"
---
# <a name="compiler-warning-level-1-c4615"></a>編譯器警告 (層級 1) C4615

\#pragma 警告：不明的使用者警告類型

搭配**pragma** [警告](../../preprocessor/warning.md)使用了不正確警告規範。 若要解決此錯誤，請使用有效的警告規範。

下列範例會產生 C4615：

```cpp
// C4615.cpp
// compile with: /W1 /LD
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier

// use the code below to resolve the error
// #pragma warning(default : 4401)
```
