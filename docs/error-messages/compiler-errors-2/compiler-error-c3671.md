---
title: 編譯器錯誤 C3671
ms.date: 11/04/2016
f1_keywords:
- C3671
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
ms.openlocfilehash: c4534b11f3aedf638f69337fb6a7af778e086bb4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778029"
---
# <a name="compiler-error-c3671"></a>編譯器錯誤 C3671

'function_1': 函式不覆寫 'function_2'

使用明確覆寫語法時，編譯器會產生錯誤，如果函式未覆寫。  請參閱[明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)如需詳細資訊。

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