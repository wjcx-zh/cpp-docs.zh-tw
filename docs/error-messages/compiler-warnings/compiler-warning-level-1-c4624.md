---
title: 編譯器警告（層級1） C4624
ms.date: 11/04/2016
f1_keywords:
- C4624
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
ms.openlocfilehash: 8ef871f31d5d1d31e6d1d26d46b6f7f99c8fba86
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051455"
---
# <a name="compiler-warning-level-1-c4624"></a>編譯器警告（層級1） C4624

'derived class'：解構函式已隱含定義為被刪除，因為基底類別解構函式無法存取或已遭刪除

解構函式無法在基底類別中存取或已遭刪除，因此無法對衍生類別產生解構函式。 在此堆疊上建立此類型物件的任何嘗試都會導致編譯器錯誤。

下列範例會產生 C4624，並顯示如何修正此問題：

```cpp
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```