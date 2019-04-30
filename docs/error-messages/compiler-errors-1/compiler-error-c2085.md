---
title: 編譯器錯誤 C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: a65e3c0ea622950b99b9ba83fc168b4718d13e46
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345714"
---
# <a name="compiler-error-c2085"></a>編譯器錯誤 C2085

'identifier': 不在型式參數清單

函式定義中，但不是在型式參數清單中，已宣告的識別項。 (ANSI C)

下列範例會產生 C2085:

```
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

可能的解決方式：

```
// C2085b.c
void func1( void );
int main( void ) {}
```

分號遺漏`func1()`看起來像函式定義，不需原型，因此`main`內定義`func1()`，產生的識別項的錯誤 C2085 `main`。