---
title: 編譯器錯誤 C3392
ms.date: 11/04/2016
f1_keywords:
- C3392
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
ms.openlocfilehash: 72bdef1b3344b3d69ba0d014f92a85e9381de4b3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776713"
---
# <a name="compiler-error-c3392"></a>編譯器錯誤 C3392

'type_arg'：對泛型參數 'param' (屬於泛型 'generic_type') 無效的類型引數，必須有公用的無參數建構函式

泛型類型未正確地具現化。 請檢查類型定義。 如需詳細資訊，請參閱 <<c0> [ 泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會使用 C#，建立包含具有 C + 中撰寫泛型類型時，不支援某些條件約束的泛型類型的元件 + CLI。 如需詳細資訊，請參閱[型別參數的條件約束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```cs
// C3392.cs
// Compile by using: csc /target:library C3392.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

C3392.dll 元件可用時，下列範例會產生 c3392:。

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