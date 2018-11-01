---
title: 編譯器錯誤 C2650
ms.date: 11/04/2016
f1_keywords:
- C2650
helpviewer_keywords:
- C2650
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
ms.openlocfilehash: c7cbc12bff4e00613032a9d28b5be7533dce9612
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607996"
---
# <a name="compiler-error-c2650"></a>編譯器錯誤 C2650

'operator': 不可為虛擬函式

A`new`或是`delete`宣告運算子`virtual`。 這些運算子`static`成員函式，而且不能是`virtual`。

## <a name="example"></a>範例

下列範例會產生 C2650:

```
// C2650.cpp
// compile with: /c
class A {
   virtual void* operator new( unsigned int );   // C2650
   // try the following line instead
   // void* operator new( unsigned int );
};
```