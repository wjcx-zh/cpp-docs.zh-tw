---
title: "如何：擷取自啟動後經過的時間 (C++/CLI) | Microsoft Docs"
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
  - "計數器, 已耗用時間"
  - "啟動"
  - "啟動, 已耗用時間"
  - "滴答計數"
  - "時間, 自啟動後所耗用的"
ms.assetid: a31fdecc-099e-4dd1-a176-f682289c5dd0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：擷取自啟動後經過的時間 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會示範如何判斷滴答計數，也就是 Windows 啟動以來經過的毫秒數。  這個值儲存在 <xref:System.Environment.TickCount%2A?displayProperty=fullName> 成員中，因為是 32 位元值，所以大約每 24.9 天會重設為零。  
  
## 範例  
  
```  
// startup_time.cpp  
// compile with: /clr  
using namespace System;  
  
int main( )   
{  
   Int32 tc = Environment::TickCount;  
   Int32 seconds = tc / 1000;  
   Int32 minutes = seconds / 60;  
   float hours = static_cast<float>(minutes) / 60;  
   float days = hours / 24;  
  
   Console::WriteLine("Milliseconds since startup: {0}", tc);  
   Console::WriteLine("Seconds since startup: {0}", seconds);  
   Console::WriteLine("Minutes since startup: {0}", minutes);  
   Console::WriteLine("Hours since startup: {0}", hours);  
   Console::WriteLine("Days since startup: {0}", days);  
  
   return 0;  
}  
```  
  
## 請參閱  
 [Windows 作業](../dotnet/windows-operations-cpp-cli.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)