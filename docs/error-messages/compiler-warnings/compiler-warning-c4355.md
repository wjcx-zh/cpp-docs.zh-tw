---
title: 編譯器警告 C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: 6b74c8dd5ce9860cb218d21790f12ba05e9be22f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554158"
---
# <a name="compiler-warning-c4355"></a>編譯器警告 C4355

'this' : 在基底成員初始設定式清單中使用

**這**指標為非靜態成員函式內才有效。 它不能在初始設定式清單之基底類別。

前受到呼叫的基底類別建構函式和類別成員建構函式**這**建構函式。 作用中，您已將指標傳送至另一個建構函式未建構的物件。 如果這些其他建構函式會存取任何成員，或呼叫此成員函式，則結果會是未定義。 您不應該使用**這**指標，直到完成所有的建構。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4355:

```
// C4355.cpp
// compile with: /w14355 /c
#include <tchar.h>

class CDerived;
class CBase {
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function() = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase {
public:
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor
   virtual void function() {};
};

CBase::~CBase() {
   m_pDerived -> function();
}

int main() {
   CDerived myDerived;
}
```