---
title: 編譯器錯誤 C2776
ms.date: 11/04/2016
f1_keywords:
- C2776
helpviewer_keywords:
- C2776
ms.assetid: 9d80addc-62c7-40fc-a2cc-60303abb87df
ms.openlocfilehash: 200fbc5c42a6b735c072c093ec4cb4f081031824
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652137"
---
# <a name="compiler-error-c2776"></a>編譯器錯誤 C2776

每個屬性，可以指定只有一個 'get' 方法

您只能指定其中一個`get`函式中[屬性](../../cpp/property-cpp.md)擴充的屬性。 會發生此錯誤時多個`get`指定函式。

下列範例會產生 C2776:

```
// C2776.cpp
struct A {
   __declspec(property(get=GetProp,get=GetPropToo))
   // try the following line instead
   // __declspec(property(get=GetProp))
      int prop;   // C2776
   int GetProp(void);
   int GetPropToo(void);
};
```