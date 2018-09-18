---
title: 編譯器警告 （層級 1） C4224 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4224
dev_langs:
- C++
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49ad5937d310166dd3ca7f41e6881d98f396535f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025655"
---
# <a name="compiler-warning-level-1-c4224"></a>編譯器警告 (層級 1) C4224

使用非標準擴充： 型式參數 'identifier' 先前已定義為類型

先前已使用的識別項當做`typedef`。 這會導致 ANSI 相容性警告 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="example"></a>範例

```
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```