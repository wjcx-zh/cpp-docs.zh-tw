---
title: 編譯器錯誤 C2498
ms.date: 11/04/2016
f1_keywords:
- C2498
helpviewer_keywords:
- C2498
ms.assetid: 0839f12c-aaa4-4a02-bb33-7f072715dd14
ms.openlocfilehash: 1087dbb2297058f752e0a15776e4a7185e32a5c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462266"
---
# <a name="compiler-error-c2498"></a>編譯器錯誤 C2498

'function': 'novtable' 只能套用至類別宣告或定義

此錯誤可能因使用`__declspec(novtable)`函式。

## <a name="example"></a>範例

下列範例會產生 C2498:

```
// C2498.cpp
// compile with: /c
void __declspec(novtable) f() {}   // C2498
class __declspec(novtable) A {};   // OK
```