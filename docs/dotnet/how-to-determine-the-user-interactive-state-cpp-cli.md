---
title: 如何： 判斷使用者互動狀態 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, user interactive state
- user interactive state
ms.assetid: 9f52323e-38b8-4a41-9b1d-052012ad839b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4649a6e7ce4833b55f38e636b87bb53f646e85cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-the-user-interactive-state-ccli"></a>如何：判斷使用者互動狀態 (C++/CLI)
下列程式碼範例示範如何判斷使用者互動的內容是否正在執行的程式碼。 如果<xref:System.Environment.UserInteractive%2A>為 false，則程式碼正在執行做為服務處理序，或從 Web 應用程式，在此情況下您不應嘗試與使用者互動。  
  
## <a name="example"></a>範例  
  
```  
// user_interactive.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   if ( Environment::UserInteractive )  
      Console::WriteLine("User interactive");  
   else  
      Console::WriteLine("Noninteractive");  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Windows 作業 (C + + /CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)