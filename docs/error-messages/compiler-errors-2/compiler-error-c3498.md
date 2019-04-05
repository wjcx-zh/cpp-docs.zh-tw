---
title: 編譯器錯誤 C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: 463e210e5a1ac5eb6d197062ed8921f9bbae4ad2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037879"
---
# <a name="compiler-error-c3498"></a>編譯器錯誤 C3498

'var': 您無法擷取的變數，其中包含 managed 或 WinRTtype

您無法擷取在 lambda 中有 managed 類型或 Windows 執行階段類型的變數。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 將 managed 或 Windows 執行階段變數傳遞至 lambda 運算式的參數清單。

## <a name="example"></a>範例

下列範例會產生 C3498，因為具有 managed 類型的變數會出現在 lambda 運算式的擷取清單中：

```
// C3498a.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [&s](String ^ r)
      { return String::Concat(s, r); } (", World!"); // C3498
}
```

## <a name="example"></a>範例

下列範例會藉由將傳遞 managed 變數 `s` 至 lambda 運算式的擷取清單中，以解析 C3498：

```
// C3498b.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [](String ^ s, String ^ r)
      { return String::Concat(s, r); } (s, ", World!");
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)