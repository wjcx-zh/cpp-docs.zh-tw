---
title: 編譯器警告 C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: 2725db0e37f8e60f37ec1b534306f516fe10be33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223339"
---
# <a name="compiler-warning-c4355"></a>編譯器警告 C4355

'this' : 在基底成員初始設定式清單中使用

**`this`** 指標只在非靜態成員函式內有效。 它不能用在基類的初始化運算式清單中。

基類的函式和類別成員的函式會在構造函式之前呼叫 **`this`** 。 實際上，您已將未建構物件的指標傳遞至另一個函式。 如果這些其他的函式會在這個上存取任何成員或呼叫成員函式，則結果會是未定義的。 您不應該使用 **`this`** 指標，直到所有結構都完成為止。

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
