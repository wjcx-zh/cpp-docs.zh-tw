---
title: 編譯器錯誤 C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: cac397e4588c493fb8c47932feb97a5f12cf2583
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578213"
---
# <a name="compiler-error-c3391"></a>編譯器錯誤 C3391

'type_arg': 對泛型參數 'param' 屬於泛型 'generic_type'，不正確的型別引數必須是不可為 null 的實值型別

泛型類型未正確地具現化。 請檢查類型定義。 如需詳細資訊，請參閱 <<c0> <xref:System.Nullable> 並[泛型](../../windows/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會使用 C#，建立包含具有 C + 中撰寫泛型類型時，不支援某些條件約束的泛型類型的元件 + CLI。 如需詳細資訊，請參閱[型別參數的條件約束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```cs
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

C3391.dll 元件可用時，下列範例會產生 C3391。

```cpp
// C3391_b.cpp
// Compile by using: cl /clr C3391_b.cpp
#using <C3391.dll>
using namespace System;
value class VClass {};

int main() {
   GR< Nullable<VClass> >^ a =
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK
}
```