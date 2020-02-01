---
title: 編譯器錯誤 C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: 7590ba9431892c07a32c27fdc97604c8b005fe33
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912861"
---
# <a name="compiler-error-c3391"></a>編譯器錯誤 C3391

' type_arg '：泛型 ' generic_type ' 泛型參數 ' param ' 的類型引數無效，必須是不可為 null 的實數值型別

泛型類型未正確地具現化。 請檢查類型定義。 如需詳細資訊，請參閱 <xref:System.Nullable> 和[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會使用C#來建立元件，其中包含的泛型型別具有在/cli 中C++撰寫泛型型別時不支援的特定條件約束 如需詳細資訊，請參閱[型別參數的條件約束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```csharp
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

當 C3391 有可用的 .dll 元件時，下列範例會產生 C3391。

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