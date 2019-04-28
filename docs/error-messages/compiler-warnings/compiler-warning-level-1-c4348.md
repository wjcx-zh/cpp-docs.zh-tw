---
title: 編譯器警告 (層級 1) C4348
ms.date: 11/04/2016
f1_keywords:
- C4348
helpviewer_keywords:
- C4348
ms.assetid: 816010eb-6079-48d5-a41b-0fc4d67cfe4c
ms.openlocfilehash: b39d5a596594367d1ca2aea17d9a752c991d06be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352883"
---
# <a name="compiler-warning-level-1-c4348"></a>編譯器警告 (層級 1) C4348

'type': 重複定義的預設參數： 參數號碼

重新定義樣板參數。

下列範例會產生 C4348:

```
// C4348.cpp
// compile with: /LD /W1
template <class T=int> struct A;   // forward declaration

template <class T=int> struct A { };
// C4348, redefinition of default parameter
// try the following line instead
// template <class T> struct A { };
```