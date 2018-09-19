---
title: 編譯器錯誤 C2085 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d88968e49e38a13782dde2d905a614ad4d177e81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082374"
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