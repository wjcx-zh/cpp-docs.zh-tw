---
title: 編譯器錯誤 C3880
ms.date: 11/04/2016
f1_keywords:
- C3880
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
ms.openlocfilehash: 54fd65fb4fe23a5c493a4e9ac83a5e44b0596362
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736668"
---
# <a name="compiler-error-c3880"></a>編譯器錯誤 C3880

' var '：不可以是常值資料成員

[常](../../extensions/literal-cpp-component-extensions.md)值屬性的類型必須是下列其中一個類型，或可轉換為的編譯時間：

- 整數類資料類型

- string

- 具有整數或基礎類型的列舉

下列範例會產生 C3880：

```cpp
// C3880.cpp
// compile with: /clr /c
ref struct Y1 {
   literal System::Decimal staticConst1 = 10;   // C3880
   literal int staticConst2 = 10;   // OK
};
```
