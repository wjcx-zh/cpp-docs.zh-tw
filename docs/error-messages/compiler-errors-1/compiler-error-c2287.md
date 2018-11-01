---
title: 編譯器錯誤 C2287
ms.date: 11/04/2016
f1_keywords:
- C2287
helpviewer_keywords:
- C2287
ms.assetid: 64556299-4e1f-4437-88b7-2464fc0b95bb
ms.openlocfilehash: f5493220c4380d1fd67b38995414f48a2ef72a41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514019"
---
# <a name="compiler-error-c2287"></a>編譯器錯誤 C2287

'class': 繼承表示: 'representation1' 是必要的 'representation2' 不可用

宣告的類別會使用比要求的簡單表示法。

下列範例會產生 C2287:

```
// C2287.cpp
// compile with: /vmg /c
class __single_inheritance X;
class __single_inheritance Y;

struct A { };
struct B { };
struct X : A, B { };  // C2287  X uses multiple inheritance
struct Y : A { };  // OK
```