---
title: 編譯器警告 （層級 1） C4114
ms.date: 11/04/2016
f1_keywords:
- C4114
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
ms.openlocfilehash: 41e951e7c4a8b23ddbec14c5421f66702e70c937
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300254"
---
# <a name="compiler-warning-level-1-c4114"></a>編譯器警告 （層級 1） C4114

相同類型的限定詞已經使用多次

類型宣告或定義使用類型限定詞 (**const**， **volatile**，**簽署**，或**不帶正負號**) 一次以上。 這會導致警告，以搭配 Microsoft 擴充功能 (/Ze) 與 ANSI 相容性 (/Za) 時發生。

下列範例會產生 C4114:

```
// C4114.cpp
// compile with: /W1 /c
volatile volatile int i;   // C4114
```

下列範例會產生 C4114:

```
// C4114_b.cpp
// compile with: /W1 /c
static const int const * ii;   // C4114
static const int * const iii;   // OK
```
