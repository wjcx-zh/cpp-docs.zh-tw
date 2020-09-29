---
title: Debug 類別 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
ms.openlocfilehash: 47e1b949cb6e998508a3bd362b1c74961cf4cc23
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414148"
---
# <a name="debug-class-ccli"></a>Debug 類別 (C++/CLI)

<xref:System.Diagnostics.Debug>在 Visual C++ 應用程式中使用時，其行為不會在 debug 和發行組建之間變更。

## <a name="remarks"></a>備註

的行為與 <xref:System.Diagnostics.Trace> Debug 類別的行為完全相同，但相依于所定義的符號追蹤。 這表示您必須 `#ifdef` 有任何追蹤相關的程式碼，以防止發行組建中的 debug 行為。

## <a name="example-always-executes-output-statements"></a>範例：一律執行 output 語句

### <a name="description"></a>描述

下列範例一律會執行 output 語句，無論您是使用 **/DDEBUG** 或 **/DTRACE**編譯。

### <a name="code"></a>程式碼

```cpp
// mcpp_debug_class.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
   Trace::Unindent();

   Debug::WriteLine("test");
}
```

### <a name="output"></a>輸出

```Output
    Entering Main
Hello World.
    Exiting Main
test
```

## <a name="example-use-ifdef-and-endif-directives"></a>範例：使用 #ifdef 和 #endif 指示詞

### <a name="description"></a>描述

若要取得預期的行為 (也就是，針對發行組建) 不會列印任何「測試」輸出，您必須使用和指示詞 `#ifdef` `#endif` 。 先前的程式碼範例修改如下以示範此修正：

### <a name="code"></a>程式碼

```cpp
// mcpp_debug_class2.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();

#ifdef TRACE   // checks for a debug build
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
#endif
   Trace::Unindent();

#ifdef DEBUG   // checks for a debug build
   Debug::WriteLine("test");
#endif   //ends the conditional block
}
```

## <a name="see-also"></a>另請參閱

[使用 c + +/CLI 進行 .NET 程式設計 (Visual C++) ](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
