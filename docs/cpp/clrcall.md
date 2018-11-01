---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: bc44feb97223de47f45734f75777ee040d0ebdd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534572"
---
# <a name="clrcall"></a>__clrcall

**Microsoft 專屬**

指定函式只可以從 Managed 程式碼呼叫。  使用 **__clrcall**只會從 managed 程式碼呼叫的所有虛擬函式。 不過，這個呼叫慣例不能用於將會從機器碼呼叫的函式。

使用 **__clrcall**呼叫虛擬 managed 函式的 managed 函式或 managed 函式透過指標的 managed 函式時，改善效能。

進入點是編譯器產生的不同函式。 如果函式同時具有原生和 Managed 進入點，則其中一個會是具有函式實作的實際函式。 另一個函式將會是呼叫實際函式內部的另一個函式 (Thunk)，並且會讓 Common Language Runtime 執行 PInvoke。 在標記為函式時 **__clrcall**，您指定的函式實作必須是 MSIL，而且將不會產生原生進入點函式。

當採用原生函式的位址，如果 **__clrcall**未指定，則編譯器會使用原生進入點。 **__clrcall**表示函式為 managed，而且沒有任何需要經歷從轉換受控到原生。 在這種情況下，編譯器會使用 Managed 進入點。

當`/clr`(不`/clr:pure`或`/clr:safe`) 會使用與 **__clrcall**是未使用，會一律採用函式的位址傳回原生進入點函式的位址。 當 **__clrcall**是使用原生進入點函式不會建立，因此您會取得 managed 函式，而不是進入點 thunk 函式的位址。 如需詳細資訊，請參閱 < [Double Thunking](../dotnet/double-thunking-cpp.md)。 **/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

[/clr （common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)表示所有函式和函式指標都 **__clrcall**編譯器不會允許要標示以外的任何編譯模組內的函式和 **__clrcall**。 當 **/clr: pure**使用，則 **__clrcall**只能在函式指標和外部宣告上指定。

您也可以直接呼叫 **__clrcall**從現有的 c + + 程式碼編譯所使用的函式 **/clr** ，只要該函式具有 MSIL 實作。 **__clrcall**函式不能直接從呼叫函式具有內嵌 asm 且呼叫 CPU 特定內，比方說，即使這些函式會編譯使用`/clr`。

**__clrcall**函式指標僅適用於所建立的應用程式定義域。  而不是傳遞 **__clrcall**函式指標跨應用程式定義域，請使用<xref:System.CrossAppDomainDelegate>。 如需詳細資訊，請參閱 <<c0> [ 應用程式定義域和 Visual c + +](../dotnet/application-domains-and-visual-cpp.md)。

## <a name="example"></a>範例

請注意，當與宣告的函式 **__clrcall**，將會在需要時，產生的程式碼; 只有在呼叫函式時，例如。

```cpp
// clrcall2.cpp
// compile with: /clr
using namespace System;
int __clrcall Func1() {
   Console::WriteLine("in Func1");
   return 0;
}

// Func1 hasn't been used at this point (code has not been generated),
// so runtime returns the adddress of a stub to the function
int (__clrcall *pf)() = &Func1;

// code calls the function, code generated at difference address
int i = pf();   // comment this line and comparison will pass

int main() {
   if (&Func1 == pf)
      Console::WriteLine("&Func1 == pf, comparison succeeds");
   else
      Console::WriteLine("&Func1 != pf, comparison fails");

   // even though comparison fails, stub and function call are correct
   pf();
   Func1();
}
```

```Output
in Func1
&Func1 != pf, comparison fails
in Func1
in Func1
```

## <a name="example"></a>範例

下列範例說明您可以定義函式指標，這樣就表示您宣告函式指標只能從 Managed 程式碼叫用。 如此編譯器就能夠直接呼叫 Managed 函式，並且避開原生進入點 (雙 Thunk 問題)。

```cpp
// clrcall3.cpp
// compile with: /clr
void Test() {
   System::Console::WriteLine("in Test");
}

int main() {
   void (*pTest)() = &Test;
   (*pTest)();

   void (__clrcall *pTest2)() = &Test;
   (*pTest2)();
}
```

## <a name="see-also"></a>另請參閱

[引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
