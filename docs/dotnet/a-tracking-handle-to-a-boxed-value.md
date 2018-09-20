---
title: Boxed 值的追蹤控制代碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxed value types, tracking handle to
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c7e26efae93b509700c3bb0c992d9f397559e99f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380722"
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>Boxed 值的追蹤控制代碼

參考實值類型的追蹤控制代碼的使用方式已經從 Managed Extensions for c + + Visual c + +。

Boxing 是整合的 CLR 型別系統的審視。 實值型別直接包含其狀態，而參考型別都是隱含的配對： 具名的實體是未命名的物件，在 managed 堆積上配置的控制代碼。 初始化或指派值的類型`Object`，比方說，需要實值型別會置於 CLR 堆積-這是其中會發生 boxing 它的映像-第一次配置相關聯的記憶體，然後藉由複製實值型別的狀態然後傳回此匿名的值/參考混合式的位址。 因此，當撰寫下列程式碼在 C#

```cpp
object o = 1024; // C# implicit boxing
```

還有許多看起來明顯來建立簡單的程式碼。 C# 的設計會隱藏複雜度不僅的哪些作業會發生在幕後，但也 boxing 本身的抽象概念。 Managed 擔心，這會導致效率的錯覺，所需要的明確指令來將它放在使用者的臉部的 c + +，相反地，擴充：

```cpp
Object *o = __box( 1024 ); // Managed Extensions explicit boxing
```

Boxing 是隱含 Visual c + +:

```cpp
Object ^o = 1024; // new syntax implicit boxing
```

`__box`關鍵字做內 Managed Extensions，另一個則是不存在的重要服務的設計語言，例如 C# 和 Visual Basic： 它提供的詞彙和追蹤的直接操作的已封裝的執行個體，在 managed 堆積上的處理。 例如，請考慮以下的小型程式：

```cpp
int main() {
   double result = 3.14159;
   __box double * br = __box( result );

   result = 2.7;
   *br = 2.17;
   Object * o = br;

   Console::WriteLine( S"result :: {0}", result.ToString() ) ;
   Console::WriteLine( S"result :: {0}", __box(result) ) ;
   Console::WriteLine( S"result :: {0}", br );
}
```

產生的三個引動過程的基礎程式碼`WriteLine`顯示成本的存取 boxed 值的輸入 （感謝 Yves Dolce 如指出這些差異)，其中指定的行顯示每個相關聯的額外負荷引動過程。

```cpp
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;
ldstr      "result :: {0}"
ldloca.s   result  // ToString overhead
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead
call       void [mscorlib]System.Console::WriteLine(string, object)

// Console::WriteLine( S"result :: {0}", __box(result) ) ;
Ldstr    " result :: {0}"
ldloc.0
box    [mscorlib]System.Double // box overhead
call    void [mscorlib]System.Console::WriteLine(string, object)

// Console::WriteLine( S"result :: {0}", br );
ldstr    "result :: {0}"
ldloc.0
call     void [mscorlib]System.Console::WriteLine(string, object)
```

直接傳遞 boxed 實的值型別`Console::WriteLine`它會消除 boxing 和叫用需要`ToString()`。 (當然，還有初始化較早的 boxing `br`，因此我們不了任何項目除非我們實際將`br`運作。

在新語法中，對 boxed 實的值類型的支援會是更加簡潔，而且型別系統中的整合式同時保留其電源。 例如，以下是舊版的小程式的轉譯：

```cpp
int main()
{
   double result = 3.14159;
   double^ br = result;
   result = 2.7;
   *br = 2.17;
   Object^ o = br;
   Console::WriteLine( "result :: {0}", result.ToString() );
   Console::WriteLine( "result :: {0}", result );
   Console::WriteLine( "result :: {0}", br );
}
```

## <a name="see-also"></a>另請參閱

[實值型別及其行為 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[如何：明確要求 Boxing](../dotnet/how-to-explicitly-request-boxing.md)