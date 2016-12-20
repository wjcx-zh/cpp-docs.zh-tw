---
title: "在舊版執行階段版本上執行 C++ /clr 應用程式 | Microsoft Docs"
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
  - "app.config 檔案, 指定的執行階段版本"
  - "應用程式部署 [C++], 指定的執行階段版本"
  - "應用程式 [C++], 指定的執行階段版本"
  - "回溯相容性 [C++], 指定的執行階段版本"
  - "common language runtime [C++], 指定的版本"
  - "相容性 [C++], 指定的執行階段版本"
  - "部署應用程式 [C++], 指定的執行階段版本"
  - "版本 [C++]"
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在舊版執行階段版本上執行 C++ /clr 應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除非特別註明，否則 Visual C\+\+ .NET Framework 應用程式在編譯器用來建立應用程式的 Common Language Runtime \(CLR\) 版本建置執行。  不過，針對執行階段的版本在其他版本中建立執行提供所需的功能的 .exe 應用程式。  
  
 若要完成這項作業，請提供在 `supportedRuntime` 標記包含執行階段版本資訊的 app.config 檔案。  
  
 在執行階段時， app.config 檔案必須有表單 *filename.ext*.config 的名稱，其中 *filename.ext* 是啟動應用程式的可執行檔的名稱，因此，它必須在與可執行檔相同。  例如，在中，如果應用程式名為 TestApp.exe， app.config 檔案的名稱是 TestApp.exe.config。  
  
 如果您指定多個執行階段版本和應用程式在有多個安裝的執行階段版本的電腦上執行時，應用程式在組態檔中指定和安裝的第一個版本。  
  
 如需詳細資訊，請參閱[How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/zh-tw/5247b307-89ca-417b-8dd0-e8f9bd2f4717)。  
  
 使用 [\/clr:initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md)，若要在 CLR 1.0 版或 1.1 版，由 Visual C\+\+ 編譯器建立的應用程式必須編譯。  
  
## 請參閱  
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)