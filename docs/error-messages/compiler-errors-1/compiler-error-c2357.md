---
title: 編譯器錯誤 C2357
ms.date: 11/04/2016
f1_keywords:
- C2357
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
ms.openlocfilehash: 1872672e776ad13bf16be5ae69729f4f68d8f3b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302029"
---
# <a name="compiler-error-c2357"></a>編譯器錯誤 C2357

'identifier': 必須是 'type' 類型的函式

您的程式碼會宣告的版本`atexit`編譯器在內部宣告的版本不符的函式。 宣告`atexit`，如下所示：

```
int __cdecl atexit(void (__cdecl *)());
```

如需詳細資訊，請參閱 < [init_seg](../../preprocessor/init-seg.md)。

下列範例會產生 C2357:

```
// C2357.cpp
// compile with: /c
// C2357 expected
#pragma warning(disable : 4075)
// Uncomment the following line to resolve.
// int __cdecl myexit(void (__cdecl *)());
#pragma init_seg(".mine$m",myexit)
```