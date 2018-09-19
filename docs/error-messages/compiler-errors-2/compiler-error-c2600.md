---
title: 編譯器錯誤 C2600 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2600
dev_langs:
- C++
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1846cefa78c8df13e8ca3c1a7fbc142ba2bf6ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022080"
---
# <a name="compiler-error-c2600"></a>編譯器錯誤 C2600

'function'：無法定義編譯器產生的特殊成員函式 (必須先在類別中宣告)

必須先在類別中宣告建構函式或解構函式之類的成員函式，才可以將它們定義給該類別。 如果未在類別中宣告任何建構函式和解構函式，則編譯器可以產生預設建構函式和解構函式 (稱為特殊成員函式)。 不過，如果您在類別中定義這其中一個函式但沒有相符的宣告，編譯器會偵測到衝突。

若要修正這個錯誤，請在類別宣告中，宣告您在類別宣告之外定義的每個成員函式。

下列範例會產生 C2600：

```
// C2600.cpp
// compile with: /c
class C {};
C::~C() {}   // C2600

class D {
   D::~D();
};

D::~D() {}
```