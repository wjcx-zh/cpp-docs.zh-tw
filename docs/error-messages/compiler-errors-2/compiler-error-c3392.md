---
title: 編譯器錯誤 C3392 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3392
dev_langs:
- C++
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04c69220cf9b6bf10a6bae8f9557f83d1e004752
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112807"
---
# <a name="compiler-error-c3392"></a>編譯器錯誤 C3392

'type_arg'：對泛型參數 'param' (屬於泛型 'generic_type') 無效的類型引數，必須有公用的無參數建構函式

泛型類型未正確地具現化。 請檢查類型定義。 如需詳細資訊，請參閱 <<c0> [ 泛型](../../windows/generics-cpp-component-extensions.md)。

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