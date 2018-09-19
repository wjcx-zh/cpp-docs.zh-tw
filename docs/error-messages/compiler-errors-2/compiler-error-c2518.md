---
title: 編譯器錯誤 C2518 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2518
dev_langs:
- C++
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 202d93e4ff466ddb1509c3d30ad3a326c07d0861
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051148"
---
# <a name="compiler-error-c2518"></a>編譯器錯誤 C2518

關鍵字 'keyword' 在基底類別清單中不合法已忽略

關鍵字`class`和`struct`不應該出現在基底的類別清單。

下列範例會產生 C2518:

```
// C2518.cpp
// compile with: /c
class B {};
class C : public class B {};   // C2518
class D: public B {};   // OK
```