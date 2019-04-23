---
title: 編譯器錯誤 C3390
ms.date: 11/04/2016
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 3f1149d4584a0ea3d0061a3ec4e2b77830603ef2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778731"
---
# <a name="compiler-error-c3390"></a>編譯器錯誤 C3390

'type_arg' : 對泛型參數 'param' (屬於泛型 'generic_type') 無效的類型引數，必須是參考類型

泛型類型未正確地具現化。  請檢查類型定義。  如需詳細資訊，請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

第一個範例會使用 C# 來建立包含具有 C + 中撰寫泛型類型時，不支援某些條件約束的泛型類型的元件 + CLR。 如需詳細資訊，請參閱[型別參數的條件約束](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)。

```cs
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

C3390.dll 元件可用時，下列範例會產生 C3390。

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