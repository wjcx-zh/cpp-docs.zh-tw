---
title: "原生和 .NET 互通性 | Microsoft Docs"
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
  - ".NET Framework [C++], 與 Visual C++ 的互通性"
  - "Interop [C++]"
  - "Interop [C++], 關於 .NET 互通性"
  - "互通性 [C++]"
  - "互通性 [C++], 關於 .NET 互通性"
  - "Managed 程式碼 [C++], 互通性"
  - "MFC [C++], .NET 整合"
  - "機器碼 [C++]"
  - "機器碼 [C++], .NET 互通性"
  - "unmanaged 程式碼互通性 [C++]"
  - "Visual C++, 互通性"
ms.assetid: f3ec6c99-c745-4256-b95b-f1d12ba17a5a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 原生和 .NET 互通性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 支援互通性 \(Interoperability\) 功能，這些功能讓 Managed 和 Unmanaged 建構可同時存在相同的組件 \(Assembly\) 並相互溝通，甚至可以在相同的檔案中。  其他的 .NET 語言也支援這個功能的小型子集 \(例如，P\/Invoke\)，但是 Visual C\+\+ 所提供的大部分互通性支援，無法在其他語言中使用。  
  
## 在本節中  
 [混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)  
 描述使用包含 Managed 和 Unmanaged 功能的 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項所產生的組件。  
  
 [在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)  
 描述如何使用 MFC Windows Form 支援類別在 MFC 應用程式內裝載 Windows Form 控制項。  
  
 [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)  
 描述如何從 .NET 應用程式使用非 CLR 的 DLL。  
  
## 請參閱  
 [\(NOTINBUILD\)Visual C\+\+ Programming Methodologies](http://msdn.microsoft.com/zh-tw/0822f806-fa81-4b65-bf0f-1e2921f30c95)