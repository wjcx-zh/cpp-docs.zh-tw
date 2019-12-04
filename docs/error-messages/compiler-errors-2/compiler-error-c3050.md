---
title: 編譯器錯誤 C3050
ms.date: 11/04/2016
f1_keywords:
- C3050
helpviewer_keywords:
- C3050
ms.assetid: ee090a0b-29cc-4215-a2f9-d82af79b8e82
ms.openlocfilehash: f8ab53974ac59de235a36e56991d2ef89f06be59
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761269"
---
# <a name="compiler-error-c3050"></a>編譯器錯誤 C3050

'type1': ref 類別不可從 'type1' 繼承

`System::ValueType` 不能是參考類型的基底類別。

下列範例會產生 C3050：

```cpp
// C3050.cpp
// compile with: /clr /LD
ref struct X : System::ValueType {};   // C3050
ref struct Y {};   // OK
```
