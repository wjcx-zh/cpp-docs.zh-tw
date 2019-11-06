---
title: 編譯器警告（層級1） C4273
ms.date: 11/04/2016
f1_keywords:
- C4273
helpviewer_keywords:
- C4273
ms.assetid: cc18611d-9454-40a4-ad73-69823d5888fb
ms.openlocfilehash: fb24f195c6a8a0b0b2a221e57508a558b50a2b96
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626677"
---
# <a name="compiler-warning-level-1-c4273"></a>編譯器警告（層級1） C4273

' function '：不一致的 DLL 連結

檔案中的兩個定義在使用[dllimport](../../cpp/dllexport-dllimport.md)時有所不同。

## <a name="example"></a>範例

下列範例會產生 C4273。

```cpp
// C4273.cpp
// compile with: /W1 /c
char __declspec(dllimport) c;
char c;   // C4273, delete this line or the line above to resolve
```

## <a name="example"></a>範例

下列範例會產生 C4273。

```cpp
// C4273_b.cpp
// compile with: /W1 /clr /c
#include <stdio.h>
extern "C" int printf_s(const char *, ...);   // C4273
```