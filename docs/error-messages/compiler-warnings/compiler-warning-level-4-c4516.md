---
title: 編譯器警告 (層級 4) C4516
ms.date: 11/04/2016
f1_keywords:
- C4516
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
ms.openlocfilehash: 8020103e8e20bf1a5e955cbfdfafc6a328b439e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564043"
---
# <a name="compiler-warning-level-4-c4516"></a>編譯器警告 (層級 4) C4516

'class::symbol': 已被取代存取宣告;成員 using 宣告代替

ANSI c + + 委員會已宣告存取宣告 (變更而不需要在衍生類別中成員的存取權[使用](../../cpp/using-declaration.md)關鍵字) 為過期。 C + + 的未來版本可能不支援存取宣告。

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