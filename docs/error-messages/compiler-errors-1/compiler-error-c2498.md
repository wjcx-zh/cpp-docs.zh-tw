---
title: 編譯器錯誤 C2498
ms.date: 11/04/2016
f1_keywords:
- C2498
helpviewer_keywords:
- C2498
ms.assetid: 0839f12c-aaa4-4a02-bb33-7f072715dd14
ms.openlocfilehash: 2b6f6469a221c914e0eef9e190c79a2b2706e651
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756990"
---
# <a name="compiler-error-c2498"></a>編譯器錯誤 C2498

' function '： ' novtable ' 只能套用至類別宣告或定義

此錯誤可能是透過使用 `__declspec(novtable)` 與函式所造成。

## <a name="example"></a>範例

下列範例會產生 C2498：

```cpp
// C2498.cpp
// compile with: /c
void __declspec(novtable) f() {}   // C2498
class __declspec(novtable) A {};   // OK
```
