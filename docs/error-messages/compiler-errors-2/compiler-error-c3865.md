---
title: 編譯器錯誤 C3865 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fd5c83d922601ca4cdffe0f3772723b31e630b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090837"
---
# <a name="compiler-error-c3865"></a>編譯器錯誤 C3865

'calling_convention': 僅適用於原生成員函式

其中一個是全域函式的函式或的受管理的成員函式上使用的呼叫慣例。 呼叫慣例僅適用於原生的 （未受管理） 成員函式。

如需詳細資訊，請參閱 <<c0> [ 呼叫慣例](../../cpp/calling-conventions.md)。

下列範例會產生 C3865:

```
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```