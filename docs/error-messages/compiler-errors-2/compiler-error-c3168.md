---
title: 編譯器錯誤 C3168
ms.date: 11/04/2016
f1_keywords:
- C3168
helpviewer_keywords:
- C3168
ms.assetid: 4c36fcfb-c351-48ff-b4eb-78d2aa1b4d55
ms.openlocfilehash: f39160cc09825c6d87d56ff5ba80d21a35f41e12
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676560"
---
# <a name="compiler-error-c3168"></a>編譯器錯誤 C3168

'type': 不合法的基礎類型列舉

基礎類型指定`enum`類型無效。 基礎類型必須是整數類資料的 c + + 類型或對應的 CLR 類型。

下列範例會產生 C3168:

```
// C3168.cpp
// compile with: /clr /c
ref class G{};

enum class E : G { e };   // C3168
enum class F { f };   // OK
```
