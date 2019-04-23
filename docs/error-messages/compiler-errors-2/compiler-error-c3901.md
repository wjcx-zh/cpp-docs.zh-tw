---
title: 編譯器錯誤 C3901
ms.date: 11/04/2016
f1_keywords:
- C3901
helpviewer_keywords:
- C3901
ms.assetid: 19af4141-39ad-4c16-a68f-3ae76f648186
ms.openlocfilehash: 31fbb1e89a0619b4dc8b3f6c86f7f6bc748b80d6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779410"
---
# <a name="compiler-error-c3901"></a>編譯器錯誤 C3901

'accessor_function': 必須有傳回類型 'type'

至少一個 get 方法的傳回類型必須符合屬性類型。 如需詳細資訊，請參閱 [property](../../extensions/property-cpp-component-extensions.md)。

下列範例會產生 C3901:

```
// C3901.cpp
// compile with: /clr /c
using namespace System;
ref class X {
   property String^ Name {
      void get();   // C3901
      // try the following line instead
      // String^ get();
   };
};

ref class Y {
   property double values[int, int] {
      int get(int, int);   // C3901
      // try the following line instead
      // double get(int, int);
   };
};
```