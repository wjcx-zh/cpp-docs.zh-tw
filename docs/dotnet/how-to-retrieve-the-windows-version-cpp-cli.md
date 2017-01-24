---
title: "如何：擷取 Windows 版本 (C++/CLI) | Microsoft Docs"
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
  - "Windows [C++], 使用 Visual C++ 擷取版本"
  - "Windows [C++], 版本"
ms.assetid: 7e6f567b-d378-49bb-aa59-2240f69a022d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：擷取 Windows 版本 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會示範如何擷取目前作業系統的平台和版本資訊。  這項資訊儲存在 <xref:System.Environment.OSVersion%2A?displayProperty=fullName> 屬性中，由使用一般性的詞彙描述 Windows 版本的列舉型別 \(Enumeration\) 和包含精確的作業系統組建 \(Build\) 之 <xref:System.Environment.Version%2A> 物件所組成。  
  
## 範例  
  
```  
// os_ver.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   OperatingSystem^ osv = Environment::OSVersion;  
   PlatformID id = osv->Platform;  
   Console::Write("Operating system: ");  
  
   if (id == PlatformID::Win32NT)  
      Console::WriteLine("Win32NT");  
   else if (id == PlatformID::Win32S)  
      Console::WriteLine("Win32S");  
   else if (id == PlatformID::Win32Windows)  
      Console::WriteLine("Win32Windows");  
   else  
      Console::WriteLine("WinCE");  
  
   Version^ version = osv->Version;  
   if (version)  
   {  
      int build = version->Build;  
      int major = version->Major;  
      int minor = version->Minor;  
      int revision = Environment::Version->Revision;  
      Console::Write("OS Version: ");  
      Console::WriteLine("{0}.{1}.{2}.{3}",   
                   build, major, minor, revision);  
   }  
  
   return 0;  
}  
```  
  
## 請參閱  
 [Windows 作業](../dotnet/windows-operations-cpp-cli.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)