---
title: 編譯器警告 C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: ddc0d1968ae373ff1e81c98a513e6f84fdb885e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165323"
---
# <a name="compiler-warning-c4355"></a>編譯器警告 C4355

'this' : 在基底成員初始設定式清單中使用

**This**指標只在非靜態成員函式內有效。 它不能用在基類的初始化運算式清單中。

基類的函式和類別成員的函式會在**此**函式之前呼叫。 實際上，您已將未建構物件的指標傳遞至另一個函式。 如果這些其他的函式會在這個上存取任何成員或呼叫成員函式，則結果會是未定義的。 您不應該使用**this**指標，直到所有結構都完成為止。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4355：

```cpp
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
