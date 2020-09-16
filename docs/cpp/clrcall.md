---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: 85e9025c26cc821cdbd8e5218e184f05e2b96b24
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685827"
---
# <a name="__clrcall"></a>__clrcall

指定函式只可以從 Managed 程式碼呼叫。  將 **__clrcall** 用於所有只從 managed 程式碼呼叫的虛擬函式。 不過，這個呼叫慣例不能用於將會從機器碼呼叫的函式。 **__Clrcall**修飾詞是 Microsoft 特定的。

使用 **__clrcall** 可改善從 managed 函式呼叫虛擬 managed 函式時的效能，或從 managed 函式透過指標從 managed 函式至 managed 函數。

進入點是編譯器產生的不同函式。 如果函式同時具有原生和 Managed 進入點，則其中一個會是具有函式實作的實際函式。 另一個函式將會是呼叫實際函式內部的另一個函式 (Thunk)，並且會讓 Common Language Runtime 執行 PInvoke。 將函式標示為 **__clrcall**時，表示函式的執行必須是 MSIL，且不會產生原生進入點函數。

如果未指定 **__clrcall** ，取得原生函式的位址時，編譯器會使用原生進入點。 **__clrcall** 表示函式是受管理的，而且不需要經過 managed 至原生的轉換。 在這種情況下，編譯器會使用 Managed 進入點。

`/clr`使用 (not `/clr:pure` 或 `/clr:safe`) 時，若未使用 **__clrcall** ，則取得函式的位址一律會傳回原生進入點函式的位址。 使用 **__clrcall** 時，不會建立原生進入點函式，因此您會取得 managed 函式的位址，而不是進入點 Thunk 函式的位址。 如需詳細資訊，請參閱 [雙重 Thunking](../dotnet/double-thunking-cpp.md)。 **/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，Visual Studio 2017 中不支援。

[/clr (Common Language Runtime 編譯) ](../build/reference/clr-common-language-runtime-compilation.md) 暗示所有函式和函式指標都是 **__clrcall** 的，而且編譯器不允許在編譯單位內將函式標記為 **__clrcall**以外的任何功能。 當使用 **/clr： pure** 時， **__clrcall** 只能在函式指標和外部宣告上指定。

只要該函式具有 MSIL 執行，您就可以直接從使用 **/clr**編譯的現有 c + + 程式碼中呼叫 **__clrcall**函式。 **__clrcall** 函式不能直接從具有內嵌 asm 的函式呼叫，以及呼叫 CPU 特定 intrinisics，例如，即使這些函式是以編譯的 `/clr` 。

**__clrcall** 函式指標只適用于其建立所在的應用程式域中。  請使用，而不是在應用程式域之間傳遞 **__clrcall** 函式指標 <xref:System.CrossAppDomainDelegate> 。 如需詳細資訊，請參閱 [應用程式域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)。

## <a name="examples"></a>範例

請注意，當使用 **__clrcall**宣告函式時，會在需要時產生程式碼;例如，呼叫函式時。

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
