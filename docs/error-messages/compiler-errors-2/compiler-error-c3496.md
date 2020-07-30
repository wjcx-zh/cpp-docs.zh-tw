---
title: 編譯器錯誤 C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 993d391f28a59afc8926748f2e6f34ab441657dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228852"
---
# <a name="compiler-error-c3496"></a>編譯器錯誤 C3496

'this' 一定以傳值方式擷取: 已忽略 '&'

您無法以傳 **`this`** 址方式來捕捉指標。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 以傳 **`this`** 值方式捕捉指標。

## <a name="example"></a>範例

下列範例會產生 C3496，因為指標的參考 **`this`** 會出現在 lambda 運算式的 capture 清單中：

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

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
