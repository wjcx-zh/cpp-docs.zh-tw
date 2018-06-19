---
title: 如何： 擷取經過的時間啟動後 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
ms.assetid: a31fdecc-099e-4dd1-a176-f682289c5dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4bebd086d24c741f0c5287e8a7fd0de6b535dfc6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132826"
---
# <a name="how-to-retrieve-time-elapsed-since-startup-ccli"></a>如何：擷取自啟動後經過的時間 (C++/CLI)
下列程式碼範例示範如何判斷滴答計數，或啟動的 Windows 以來經過的毫秒數。 這個值會儲存在<xref:System.Environment.TickCount%2A?displayProperty=fullName>成員，因為它是 32 位元值，會重設為零大約每隔 24.9 天。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱  
 [Windows 作業 (C + + /CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)