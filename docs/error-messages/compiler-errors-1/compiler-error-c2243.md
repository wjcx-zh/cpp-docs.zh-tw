---
title: 編譯器錯誤 C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: ab0dbe8c5595c18a01f78c22056803dce91a3f31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212835"
---
# <a name="compiler-error-c2243"></a>編譯器錯誤 C2243

'conversion type' 從 'type1' 至 'type2' 的轉換已經存在，但無法存取

存取保護（ **`protected`** 或 **`private`** ）防止從衍生類別的指標轉換為基類的指標。

下列範例會產生 C2243：

```cpp
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

**`protected`** **`private`** 衍生類別的用戶端無法存取具有或存取的基類。 這些層級的存取控制是用來指出基底類別是用戶端應該看到的實作細節。 如果您希望衍生類別的用戶端可以存取衍生類別指標對基底類別指標的隱含轉換，請使用公用衍生。
