---
title: 編譯器錯誤 C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 025498f3fe244916cd0a06e36feee6fdb532acc6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026685"
---
# <a name="compiler-error-c3496"></a>編譯器錯誤 C3496

'this' 一定以傳值方式擷取: 已忽略 '&'

您不能以傳址方式來擷取 `this` 指標。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 請以傳值方式來擷取 `this` 指標。

## <a name="example"></a>範例

下列範例會產生 C3496，因為 `this` 指標的參考出現在 Lambda 運算式的擷取清單中：

```
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

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)