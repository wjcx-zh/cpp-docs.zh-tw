---
title: 編譯器錯誤 C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: 771e8c72ab4386bb45a11983318f412e784f5bc9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738098"
---
# <a name="compiler-error-c3498"></a>編譯器錯誤 C3498

' var '：您無法捕獲具有 managed 或 WinRTtype 的變數

您無法擷取在 lambda 中有 managed 類型或 Windows 執行階段類型的變數。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

- 將 managed 或 Windows 執行階段變數傳遞至 lambda 運算式的參數清單。

## <a name="example"></a>範例

下列範例會產生 C3498，因為具有 managed 類型的變數會出現在 lambda 運算式的擷取清單中：

```cpp
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

```cpp
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

## <a name="see-also"></a>請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)
