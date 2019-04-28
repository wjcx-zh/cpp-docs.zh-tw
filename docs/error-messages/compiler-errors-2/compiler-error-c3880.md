---
title: 編譯器錯誤 C3880
ms.date: 11/04/2016
f1_keywords:
- C3880
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
ms.openlocfilehash: 0b169309db88291f8a83b6d1192787b6396e84a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338463"
---
# <a name="compiler-error-c3880"></a>編譯器錯誤 C3880

'var': 不可以是常值資料成員

型別[常值](../../extensions/literal-cpp-component-extensions.md)必須是屬性，或編譯時期轉換成下列類型之一：

- 整數類資料類型

- 字串

- 整數或基礎類型的列舉

下列範例會產生 C3880:

```
// C3880.cpp
// compile with: /clr /c
ref struct Y1 {
   literal System::Decimal staticConst1 = 10;   // C3880
   literal int staticConst2 = 10;   // OK
};
```