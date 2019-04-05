---
title: 編譯器錯誤 C3666
ms.date: 11/04/2016
f1_keywords:
- C3666
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
ms.openlocfilehash: edca117da585fee731041d696e05af1baf6d3e5c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778672"
---
# <a name="compiler-error-c3666"></a>編譯器錯誤 C3666

'constructor': 覆寫規範 'keyword' 不允許在建構函式

在建構函式，使用覆寫規範和不允許。 如需詳細資訊，請參閱 <<c0> [ 覆寫規範](../../extensions/override-specifiers-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3666。

```
// C3666.cpp
// compile with: /clr /c
ref struct R {
   R() new {}   // C3666
   R(int i) {}   // OK
};
```