---
title: Debug 類別 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
ms.openlocfilehash: 3a262a0d2ef429cb94f4648eb7c7180e7b130279
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743616"
---
# <a name="debug-class-ccli"></a>Debug 類別 (C++/CLI)

當使用<xref:System.Diagnostics.Debug>Visual c + + 應用程式中，行為之間都沒有變更偵錯和發行組建。

## <a name="remarks"></a>備註

行為<xref:System.Diagnostics.Trace>等同於偵錯類別的行為，但取決於追蹤所定義的符號。 這表示，您必須使用`#ifdef`任何追蹤相關的程式碼，以避免在發行組建的偵錯行為。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例會永遠執行輸出陳述式，不論您是否使用編譯 **/DDEBUG**或是 **/DTRACE**。

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

## <a name="example"></a>範例

### <a name="description"></a>描述

若要取得預期的行為 （亦即，沒有 「 測試 」 的輸出列印的發行組建），您必須使用`#ifdef`和`#endif`指示詞。 為了示範此修正，上述的程式碼範例會修改如下：

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

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
