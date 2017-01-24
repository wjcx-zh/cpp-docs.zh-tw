---
title: "如何：擷取目前的使用者名稱 (C++/CLI) | Microsoft Docs"
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
  - "目前的使用者名稱"
  - "使用者名稱, 擷取"
  - "UserName 字串"
ms.assetid: 91679571-d029-41f5-b657-1460c81c608a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：擷取目前的使用者名稱 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例會示範擷取目前的使用者名稱 \(登入至 Windows 的使用者名稱\)。  名稱會儲存在 <xref:System.Environment.UserName%2A> 字串中，此字串定義在 <xref:System.Environment> 命名空間中。  
  
## 範例  
  
```  
// username.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);  
   return 0;  
}  
```  
  
## 請參閱  
 [Windows 作業](../dotnet/windows-operations-cpp-cli.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)