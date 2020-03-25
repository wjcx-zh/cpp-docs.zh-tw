---
title: 編譯器錯誤 C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 0289d49ebbb0e30153beb6b0b2bc758bff5ef118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201301"
---
# <a name="compiler-error-c3320"></a>編譯器錯誤 C3320

'type': 類型不可擁有與模組 'name' 屬性相同的名稱

匯出的使用者定義型別（UDT）可以是結構、類別、列舉或等位，其名稱不能與傳遞給[module](../../windows/module-cpp.md)屬性之 name 屬性的參數同名。

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
