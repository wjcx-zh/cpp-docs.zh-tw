---
title: 如何：使用泛型改善效能 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
ms.openlocfilehash: 039c5b069351249e51d961d9d1757ed6b09ef99c
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414161"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>如何：使用泛型改善效能 (C++/CLI)

使用泛型可以根據型別參數建立可重複使用的程式碼。 型別參數的實際類型會延後，直到用戶端程式碼呼叫它為止。 如需泛型的詳細資訊，請參閱 [Generics](generics-cpp-component-extensions.md)。

本文將討論泛型如何協助使用集合的應用程式提升效能。

## <a name="example-two-main-drawbacks-of-net-framework-collections"></a>範例： .NET Framework 集合的兩個主要缺點

.NET Framework 的 <xref:System.Collections?displayProperty=fullName> 命名空間中隨附了許多集合類別。 這些集合大部分可用於 <xref:System.Object?displayProperty=fullName> 類型的物件。 這可讓集合儲存任何類型，因為 .NET Framework 中的所有類型 (甚至是實值類型) 都是衍生自 <xref:System.Object?displayProperty=fullName>。 然而，這個方法有兩個缺點。

一個缺點是，如果集合將實值類型儲存為整數，則該值必須先進行 Boxed 處理，才能加入至集合，而且從集合中擷取值時，要先進行 Unboxed 處理。 這些都是相當耗資源的作業。

另一個缺點是沒有辦法控制可加入至集合的類型。 將整數和字串加入至相同集合中完全合法，即使這可能不是您想要的結果。 因此，為了讓您的程式碼具備類型安全，您必須檢查從集合擷取的類型是否確實是預期的類型。

在泛型之前，下列程式碼範例將先示範 .NET Framework 集合的這兩個主要缺點。

```cpp
// perf_pre_generics.cpp
// compile with: /clr

using namespace System;
using namespace System::Collections;

int main()
{
    // This Stack can contain any type.
    Stack ^s = gcnew Stack();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);

    // Push a String to the same Stack.
    // The Stack now contains two different data types.
    s->Push("Seven");

    // Pop the items off the Stack.
    // The item is returned as an Object, so a cast is
    // necessary to convert it to its proper type.
    while (s->Count> 0)
    {
        Object ^o = s->Pop();
        if (o->GetType() == Type::GetType("System.String"))
        {
            Console::WriteLine("Popped a String: {0}", (String ^)o);
        }
        else if (o->GetType() == Type::GetType("System.Int32"))
        {
            Console::WriteLine("Popped an int: {0}", (int)o);
        }
        else
        {
            Console::WriteLine("Popped an unknown type!");
        }
    }
}
```

```Output
Popped a String: Seven
Popped an int: 7
```

## <a name="example-benefit-of-using-generic-collection"></a>範例：使用泛型集合的優點

新的 <xref:System.Collections.Generic?displayProperty=fullName> 命名空間包含許多與 <xref:System.Collections?displayProperty=fullName> 命名空間中相同的集合，不過，這些集合已經過修改，可接受泛型類型參數。 這樣就可解決非泛型集合的兩個缺點：實值類型的 Boxing 和 Unboxing，以及無法指定儲存在集合中的類型。 這兩個集合的作業方式相同，只有具現化的方式不同。

請與這個範例前段使用泛型 <xref:System.Collections.Generic.Stack%601> 集合撰寫的範例做比較。 對於經常存取的大型集合而言，這個範例的效能將明顯高於前一個範例。

```cpp
// perf_post_generics.cpp
// compile with: /clr

#using <System.dll>

using namespace System;
using namespace System::Collections::Generic;

int main()
{
    // This Stack can only contain integers.
    Stack<int> ^s = gcnew Stack<int>();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);
    s->Push(14);

    // You can no longer push a String to the same Stack.
    // This will result in compile time error C2664.
    //s->Push("Seven");

    // Pop an item off the Stack.
    // The item is returned as the type of the collection, so no
    // casting is necessary and no unboxing is performed for
    // value types.
    int i = s->Pop();
    Console::WriteLine(i);

    // You can no longer retrieve a String from the Stack.
    // This will result in compile time error C2440.
    //String ^str = s->Pop();
}
```

```Output
14
```

## <a name="see-also"></a>另請參閱

[泛型](generics-cpp-component-extensions.md)
