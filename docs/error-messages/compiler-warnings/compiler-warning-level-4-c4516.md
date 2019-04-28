---
title: 編譯器警告 (層級 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 8020103e8e20bf1a5e955cbfdfafc6a328b439e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221029"
---
# <a name="compiler-warning-level-4-c4516"></a>編譯器警告 (層級 4) C4516

'class::symbol': 已被取代存取宣告;成員 using 宣告代替

ANSIC++委員會已宣告存取宣告 (變更而不需要在衍生類別中成員的存取權[使用](../../cpp/using-declaration.md)關鍵字) 為過期。 存取宣告可能不會受到未來版本的C++。

下列範例會產生 C4516:

```
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