---
title: 編譯器錯誤 C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 98af3c84b48aa8e69ad883bf73299f2697618ce1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501339"
---
# <a name="compiler-error-c3320"></a>編譯器錯誤 C3320

'type': 類型不可擁有與模組 'name' 屬性相同的名稱

匯出的使用者定義型別 (UDT) （可能是結構、類別、列舉或等位）的名稱不能與傳遞給 [模組](../../windows/attributes/module-cpp.md) 屬性名稱屬性的參數相同。

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
