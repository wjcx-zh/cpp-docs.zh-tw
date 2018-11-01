---
title: 編譯器錯誤 C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 622e7366dda4cd6693d9b6128855fa0966e07952
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581463"
---
# <a name="compiler-error-c3320"></a>編譯器錯誤 C3320

'type': 類型不可擁有與模組 'name' 屬性相同的名稱

匯出的使用者定義型別 (UDT)，可能是結構、 類別、 列舉或等位，不能有相同的名稱，將參數傳遞至[模組](../../windows/module-cpp.md)屬性的名稱屬性。

## <a name="example"></a>範例

下列範例會產生 C3320：

```cpp
// C3320.cpp
#include "unknwn.h"
[module(name="xx")];

[export] struct xx {   // C3320
// Try the following line instead
// [export] struct yy {
   int i;
};
```