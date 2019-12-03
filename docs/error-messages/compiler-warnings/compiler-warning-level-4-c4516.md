---
title: 編譯器警告 (層級 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 23e1ec488a661e68d5b53fba50661354182a1015
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683169"
---
# <a name="compiler-warning-level-4-c4516"></a>編譯器警告 (層級 4) C4516

' class：： symbol '：存取聲明已被取代;使用宣告的成員可以提供更好的替代方案

ANSI C++委員會已宣告存取宣告（在不[使用](../../cpp/using-declaration.md)關鍵字的情況下變更衍生類別中成員的存取權）會過時。 未來的C++版本可能不支援存取宣告。

下列範例會產生 C4516：

```cpp
// C4516.cpp
// compile with: /W4
class A
{
public:
   void x(char);
};

class B : protected A
{
public:
   A::x;  // C4516 on access-declaration
   // use the following line instead
   // using A::x; // using-declaration, ok
};

int main()
{
}
```