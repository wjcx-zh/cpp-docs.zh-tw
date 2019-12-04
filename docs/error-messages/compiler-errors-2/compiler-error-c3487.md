---
title: 編譯器錯誤 C3487
ms.date: 11/04/2016
f1_keywords:
- C3487
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
ms.openlocfilehash: 7b38755470e3746066711382b2ed471badc8e197
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738436"
---
# <a name="compiler-error-c3487"></a>編譯器錯誤 C3487

'return type'：所有傳回運算式必須推算為相同類型：先前是 'return type'

Lambda 必須指定其傳回型別，除非它包含單一 return 陳述式。 如果 Lambda 包含多個 return 陳述式，則必須有相同的類型。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

- 指定 Lambda 的尾端傳回型別。 確認所有從 Lambda 的傳回類型皆相同，或是隱含地轉換為傳回類型。

## <a name="example"></a>範例

下列範例會產生 C3487，因為 Lambda 的傳回型別不相符：

```cpp
// C3487.cpp
// Compile by using: cl /c /W4 C3487.cpp

int* test(int* pi) {
   // To fix the error, uncomment the trailing return type below
   auto odd_pointer = [=]() /* -> int* */ {
      if (*pi % 2)
         return pi;
      return nullptr; // C3487 - nullptr is not an int* type
   };
   return odd_pointer();
}
```

## <a name="see-also"></a>請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
