---
title: 編譯器錯誤 C2650
ms.date: 11/04/2016
f1_keywords:
- C2650
helpviewer_keywords:
- C2650
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
ms.openlocfilehash: f71996c6d04d8be2101762fb0fb17634e6b25a1a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756132"
---
# <a name="compiler-error-c2650"></a>編譯器錯誤 C2650

' operator '：不可以是虛擬函式

`new` 或 `delete` 運算子會 `virtual`宣告。 這些運算子是 `static` 成員函式，無法 `virtual`。

## <a name="example"></a>範例

下列範例會產生 C2650：

```cpp
// C2650.cpp
// compile with: /c
class A {
   virtual void* operator new( unsigned int );   // C2650
   // try the following line instead
   // void* operator new( unsigned int );
};
```
