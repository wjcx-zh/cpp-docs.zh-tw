---
title: 變數引數清單 (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: 8ea4d71bf9a22fc96c794a92ba43bed6548cf5d1
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032300"
---
# <a name="variable-argument-lists--ccli"></a>變數引數清單 (...) (C++/CLI)

此範例示範如何在 C++/CLI 中使用 `...` 語法來實作含有可變數目之引數的函式。

> [!NOTE]
> 本主題適用於 C++/CLI。 有關在 ISO`...`標準 C++中使用 的資訊,請參閱[省略號和可變範本](../cpp/ellipses-and-variadic-templates.md)以及[「後修復」表達式](../cpp/postfix-expressions.md)中的省略號和省略號和默認參數。

使用 `...` 的參數必須是參數清單中的最後一個參數。

## <a name="example"></a>範例

### <a name="code"></a>程式碼

```cpp
// mcppv2_paramarray.cpp
// compile with: /clr
using namespace System;
double average( ... array<Int32>^ arr ) {
   int i = arr->GetLength(0);
   double answer = 0.0;

   for (int j = 0 ; j < i ; j++)
      answer += arr[j];

   return answer / i;
}

int main() {
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));
}
```

```Output
3
```

## <a name="code-example"></a>程式碼範例

下列範例示範如何從 C# 呼叫採用可變數目之引數的 Visual C++ 函式。

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

函式 `f` 可從 C# 或 Visual Basic 中呼叫，例如，就好像它是可採用可變數目之引數的函式一樣。

在 C# 中，傳遞給 `ParamArray` 參數的引數可以透過可變數目的引數來呼叫。 下列為 C# 程式碼範例。

```csharp
// mcppv2_paramarray3.cs
// compile with: /r:mcppv2_paramarray2.dll
// a C# program

public class X {
   public static void Main() {
      // Visual C# will generate a String array to match the
      // ParamArray attribute
      C myc = new C();
      myc.f("hello", "there", "world");
   }
}
```

在 Visual C++ 中呼叫 `f` 可傳遞初始化的陣列或可變長度的陣列。

```cpp
// mcpp_paramarray4.cpp
// compile with: /clr
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};

int main() {
   C ^ myc = gcnew C();
   myc->f("hello", "world", "!!!");
}
```

## <a name="see-also"></a>另請參閱

[陣列](arrays-cpp-component-extensions.md)
