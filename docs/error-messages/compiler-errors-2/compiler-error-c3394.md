---
title: 編譯器錯誤 C3394
ms.date: 11/04/2016
f1_keywords:
- C3394
helpviewer_keywords:
- C3394
ms.assetid: 4e025d79-27ba-43c8-b0d9-839ecef98126
ms.openlocfilehash: 4eba2c9f34f1cfcaf97733f914520043ee1124bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557389"
---
# <a name="compiler-error-c3394"></a>編譯器錯誤 C3394

條件約束子句中語法錯誤：找到 'identifier'，但必須是類型

條件約束的格式錯誤。  如需詳細資訊，請參閱 <<c0> [ 泛型類型參數的條件約束 (C + + /cli CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3394：

```
// C3394.cpp
// compile with: /clr /c
ref class MyClass {};
ref class R {
   generic<typename T>
   where T : static   // C3394
   // try the following line instead
   // where T : MyClass
   void f() {}
};
```