---
title: 編譯器錯誤 C2337
ms.date: 11/04/2016
f1_keywords:
- C2337
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
ms.openlocfilehash: 63f18a12ccd1962dd221324f5557c29be89eb04c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188268"
---
# <a name="compiler-error-c2337"></a>編譯器錯誤 C2337

'attribute name': 找不到屬性

您已使用在這個版本的 Visual C++ 中不受支援的屬性。

下列範例會產生 C2337：

```
// C2337.cpp
// compile with: /c
[emitidl];
[module(name="x")];
[grasshopper]   // C2337, not a supported attribute
class a{};
```