---
title: 編譯器錯誤 C2815
ms.date: 11/04/2016
f1_keywords:
- C2815
helpviewer_keywords:
- C2815
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
ms.openlocfilehash: ab6708e7ae0a56bd71adebad4fb42d6ea9abe116
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432652"
---
# <a name="compiler-error-c2815"></a>編譯器錯誤 C2815

'operator delete': 第一型式參數必須是 ' void *'，但使用 'param'

任何使用者定義[delete 運算子](../../standard-library/new-operators.md#op_delete)函式必須接受類型的第一個型式參數`void *`。

下列範例會產生 C2815:

```
// C2815.cpp
// compile with: /c
class CMyClass {
public:
   void mf1(int *a);
   void operator delete(CMyClass *);   // C2815
   void operator delete(void *);
};
```