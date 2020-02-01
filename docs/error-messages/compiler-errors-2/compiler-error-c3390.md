---
title: 編譯器錯誤 C3390
ms.date: 11/04/2016
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: c624d3b0379d057b0ed566deffc2a0efcc324f88
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912866"
---
# <a name="compiler-error-c3390"></a>編譯器錯誤 C3390

'type_arg' : 對泛型參數 'param' (屬於泛型 'generic_type') 無效的類型引數，必須是參考類型

泛型類型未正確地具現化。  請檢查類型定義。  如需詳細資訊，請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

第一個範例會C#使用來建立元件，其中包含的泛型型別具有在/clr 中C++撰寫泛型型別時不支援的特定條件約束 如需詳細資訊，請參閱[型別參數的條件約束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

當 C3390 有可用的 .dll 元件時，下列範例會產生 C3390。

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK
}
```