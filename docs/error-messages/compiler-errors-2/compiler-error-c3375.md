---
title: 編譯器錯誤 C3375
ms.date: 11/04/2016
f1_keywords:
- C3375
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
ms.openlocfilehash: ba1dbf08fb56364d2ab5b8c40847ab89484dc005
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776401"
---
# <a name="compiler-error-c3375"></a>編譯器錯誤 C3375

'function' : 模稜兩可的委派函式

委派具現化可能已指派給靜態成員函式，或作為執行個體函式的未繫結委派，因此編譯器會發出這個錯誤。

如需詳細資訊，請參閱 <<c0> [ 委派 (C++元件擴充功能)](../../extensions/delegate-cpp-component-extensions.md)。</c0>

## <a name="example"></a>範例

下列範例會產生 C3375。

```
// C3375.cpp
// compile with: /clr
ref struct R {
   static void f(R^) {}
   void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::f);   // C3375
}
```