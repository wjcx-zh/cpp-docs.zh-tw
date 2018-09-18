---
title: 編譯器錯誤 C3671 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3671
dev_langs:
- C++
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 455b9e2a6accbc98ee8bce49a35a672d9cd9c20d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017063"
---
# <a name="compiler-error-c3671"></a>編譯器錯誤 C3671

'function_1': 函式不覆寫 'function_2'

使用明確覆寫語法時，編譯器會產生錯誤，如果函式未覆寫。  請參閱[明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3671。

```
// C3671.cpp
// compile with: /clr /c
ref struct S {
   virtual void f();
};

ref struct S1 : S {
   virtual void f(int) new sealed = S::f;   // C3671
   virtual void f() new sealed = S::f;
};
```