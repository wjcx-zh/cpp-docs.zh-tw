---
title: 編譯器錯誤 C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: b9542f1904c6797a77c88c88a37aff9348364268
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738176"
---
# <a name="compiler-error-c3496"></a>編譯器錯誤 C3496

'this' 一定以傳值方式擷取: 已忽略 '&'

您不能以傳址方式來擷取 `this` 指標。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

- 請以傳值方式來擷取 `this` 指標。

## <a name="example"></a>範例

下列範例會產生 C3496，因為 `this` 指標的參考出現在 Lambda 運算式的擷取清單中：

```cpp
// C3496.cpp
// compile with: /c

class C
{
   void f()
   {
      [&this] {}(); // C3496
   }
};
```

## <a name="see-also"></a>請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
