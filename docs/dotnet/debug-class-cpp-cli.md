---
title: "Debug 類別 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET Framework [C++], Debug 類別"
  - "Debug 類別"
  - "Trace 類別, Visual C++"
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Debug 類別 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual C\+\+ 應用程式中使用 <xref:System.Diagnostics.Debug> 時，偵錯的組建 \(Debug Build\) 和發行的組建 \(Release Build\) 之間行為並未變更。  
  
## 備註  
 <xref:System.Diagnostics.Trace> 的行為與偵錯類別的行為完全相同，只是必須根據所定義的符號 TRACE 而定，  也就是說，您必須使用 `#ifdef` 定義任何與 Trace 相關的程式碼，才可以在發行的組建中避免偵錯行為。  
  
## 範例  
  
### 說明  
 下列範例一定會執行輸出陳述式，不論您是以 **\/DDEBUG** 還是 **\/DTRACE** 進行編譯。  
  
### 程式碼  
  
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
  
### Output  
  
```  
    Entering Main  
Hello World.  
    Exiting Main  
test  
```  
  
## 範例  
  
### 說明  
 若要達到預期的行為 \(也就是不為發行的組建列印 "test" 輸出\)，您必須使用 `#ifdef` 和 `#endif` 指示詞。  以下是之前程式碼範例的修正，以示範這種修復 \(Fix\)：  
  
### 程式碼  
  
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
  
## 請參閱  
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)