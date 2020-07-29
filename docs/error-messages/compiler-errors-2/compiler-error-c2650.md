---
title: 編譯器錯誤 C2650
ms.date: 11/04/2016
f1_keywords:
- C2650
helpviewer_keywords:
- C2650
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
ms.openlocfilehash: 102c6f713027917104cd46894fad0775076359c9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216137"
---
# <a name="compiler-error-c2650"></a>編譯器錯誤 C2650

' operator '：不可以是虛擬函式

**`new`** 已宣告 or **`delete`** 運算子 **`virtual`** 。 這些運算子是 **`static`** 成員函式，而且不能是 **`virtual`** 。

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
