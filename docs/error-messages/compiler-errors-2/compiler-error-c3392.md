---
title: 編譯器錯誤 C3392
ms.date: 11/04/2016
f1_keywords:
- C3392
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
ms.openlocfilehash: 31975d39d67697573af7f9142326660acc4f7226
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201041"
---
# <a name="compiler-error-c3392"></a>編譯器錯誤 C3392

'type_arg'：對泛型參數 'param' (屬於泛型 'generic_type') 無效的類型引數，必須有公用的無參數建構函式

泛型類型未正確地具現化。 請檢查類型定義。 如需詳細資訊，請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會使用C#來建立元件，其中包含的泛型型別具有在/cli 中C++撰寫泛型型別時不支援的特定條件約束 如需詳細資訊，請參閱[型別參數的條件約束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```csharp
// C3392.cs
// Compile by using: csc /target:library C3392.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

當 C3392 有可用的 .dll 元件時，下列範例會產生 C3392。

```cpp
// C3392_b.cpp
// Compile by using: cl /clr C3392_b.cpp
#using <C3392.dll>

ref class R { R(int) {} };
ref class N { N() {} };

value class V {};

ref class N2 { public: N2() {} };
ref class R2 { public: R2() {} };

int main () {
   GR<R^, V, N^>^ gr1;   // C3392
   GR<R^, V, N2^>^ gr1a; // OK

   GR<R^, N^, N^>^ gr3;  // C3392
   GR<R^, V, N2^>^ gr3a; // OK

   GR<R^, V, R^>^ gr4;   // C3392
   GR<R^, V, R2^>^ gr4a; // OK
}
```
