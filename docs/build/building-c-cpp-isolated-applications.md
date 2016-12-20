---
title: "建置 C/C++ 隔離應用程式 | Microsoft Docs"
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
  - "隔離的應用程式 [C++]"
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建置 C/C++ 隔離應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

隔離應用程式只依賴並存組件，並使用資訊清單繫結至它的相依檔案。  不需要將應用程式完全隔離，也可以在 Windows 上適當地執行；但是，當您讓應用程式完全隔離時，可以在未來需要服務應用程式時節省時間。  如需讓應用程式完全隔離之優點的詳細資訊，請參閱[隔離應用程式 \[Windows Installer\]](http://msdn.microsoft.com/library/aa375190)。  
  
 當您使用 Visual C\+\+ 建置原生 C\/C\+\+ 應用程式時，根據預設，Visual Studio 專案系統會產生一個資訊清單檔，此檔案會描述該應用程式對於 Visual C\+\+ 程式庫的相依性。  如果此應用程式只有這些相依性，那麼您只要以 Visual Studio 重新建置此應用程式，它就會成為隔離應用程式。  如果應用程式在執行階段使用其他程式庫，則可能必須將這些程式庫重新建置為並存組件 \(遵循[建置 C\/C\+\+ 並存組件](../build/building-c-cpp-side-by-side-assemblies.md)中的步驟\)。  
  
## 請參閱  
 [隔離應用程式和並存組件的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [建置 C\/C\+\+ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)