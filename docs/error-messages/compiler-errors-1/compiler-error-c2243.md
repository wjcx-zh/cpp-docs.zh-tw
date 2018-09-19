---
title: 編譯器錯誤 C2243 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2243
dev_langs:
- C++
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef5d3a6c20ff147ac2a4b765c7779cec9f19627e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102225"
---
# <a name="compiler-error-c2243"></a>編譯器錯誤 C2243

'conversion type' 從 'type1' 至 'type2' 的轉換已經存在，但無法存取

存取保護 (`protected` 或 `private`) 會防止從衍生類別的指標轉換為基底類別的指標。

下列範例會產生 C2243：

```
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

`protected` 或 `private` 存取的基底類別無法供衍生類別的用戶端存取。 這些層級的存取控制是用來指出基底類別是用戶端應該看到的實作細節。 如果您希望衍生類別的用戶端可以存取衍生類別指標對基底類別指標的隱含轉換，請使用公用衍生。