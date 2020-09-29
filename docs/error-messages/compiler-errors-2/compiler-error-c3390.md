---
title: 編譯器錯誤 C3390
description: Microsoft c + + 編譯器錯誤 C3390、其原因和解決方式。
ms.date: 09/26/2020
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 467b379d7f5a349a217b566dc55b28d5fbd789da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414356"
---
# <a name="compiler-error-c3390"></a>編譯器錯誤 C3390

> '*type_arg*'：對泛型參數 '*param*' （屬於泛型 '*generic_type*'）不正確類型引數，必須是參考型別

泛型類型未正確地具現化。 請檢查類型定義。

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

第一個範例會使用 c # 來建立包含泛型型別的元件。 此類型具有在 c + + 中撰寫泛型型別時不支援的特定條件約束/CLI 如需詳細資訊，請參閱[型別參數的條件約束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

當 C3390.dll 元件可供使用時，下列範例會產生 C3390。

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK - do this instead
}
```
