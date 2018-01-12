---
title: "Debug 類別 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 236a40873d3cbd660f9999880d46df4f91632b2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="debug-class-ccli"></a>Debug 類別 (C++/CLI)
當使用<xref:System.Diagnostics.Debug>Visual c + + 應用程式中的行為不會偵錯和發行組建之間變更。  
  
## <a name="remarks"></a>備註  
 行為<xref:System.Diagnostics.Trace>偵錯類別的行為相同，但是相依於追蹤所定義的符號。 這表示，您必須使用`#ifdef`任何與追蹤相關的程式碼來避免在發行組建的偵錯行為。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例執行的速度輸出陳述式，不論您是否使用編譯**/DDEBUG**或**/DTRACE**。  
  
### <a name="code"></a>程式碼  
  
```  
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
  
```  
    Entering Main  
Hello World.  
    Exiting Main  
test  
```  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 若要取得預期的行為 （也就是沒有 「 測試 」 的輸出列印的發行組建），您必須使用`#ifdef`和`#endif`指示詞。 上述程式碼範例示範此修正修改如下：  
  
### <a name="code"></a>程式碼  
  
```  
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
  
## <a name="see-also"></a>請參閱  
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)