---
title: "部署概念 | Microsoft Docs"
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
  - "應用程式部署 [C++], 關於應用程式部署"
  - "相依性 [C++], 應用程式部署和"
  - "部署應用程式 [C++], 關於部署應用程式"
  - "程式庫 [C++], 應用程式部署問題"
  - "Windows Installer [C++]"
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 部署概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本章節討論部署 C\+\+ 應用程式的主要考量。  
  
## C\+\+ 中的 Windows Installer 部署  
 Visual C\+\+ 專案通常會使用傳統的 Windows Installer 安裝程式做為部署工具。  若要準備 Windows Installer 部署，您需要將應用程式封裝到 setup.exe 檔中，並將該檔與安裝程式套件 \(.msi\) 一起散發。  然後，使用者會執行 setup.exe 來安裝應用程式。  
  
 您可以將安裝專案加入到方案中，以封裝應用程式；當建置時，它會建立散發給使用者的安裝和安裝程式套件檔案。  如需詳細資訊，請參閱[選擇部署方法](../ide/choosing-a-deployment-method.md)。  
  
## 程式庫相依性  
 當使用 Visual C\+\+ 程式庫所提供的功能來建置 C\/C\+\+ 應用程式時，它會在執行階段依賴這些程式庫的存在。  為了要讓應用程式執行，它必須以靜態或動態方式連結到所需的 Visual C\+\+ 程式庫。  如果應用程式動態連結到 Visual C\+\+ 程式庫，則當它執行時，該程式庫必須存在，才能將其載入。  另一方面，如果應用程式靜態連結到 Visual C\+\+ 程式庫，則它不需要對應的 DLL 存在於使用者的電腦上。  但是，靜態連結有一些負面的作用，例如增加應用程式檔案的大小，以及可能會讓維護作業變得更困難。  如需詳細資訊，請參閱[使用 DLL 的優點](../build/advantages-of-using-dlls.md)。  
  
## 封裝和轉散發  
 Visual C\+\+ 程式庫會封裝為 DLL，且 C\/C\+\+ 應用程式的所有必要程式庫會由 Visual Studio 安裝在開發人員的電腦上。  然而，將應用程式部署至使用者時，在大部分的情況下，不太可能為了要執行您的應用程式就要求他們安裝 Visual Studio。  很重要的一點是，只能轉散發應用程式所需的 Visual C\+\+ 部分，才能正確執行。  
  
 如需有關封裝和轉散發的詳細資訊，請參閱下列主題：  
  
-   [決定要轉散發哪些 DLL](../ide/determining-which-dlls-to-redistribute.md).  
  
-   [選擇部署方法](../ide/choosing-a-deployment-method.md).  
  
 如需部署範例和疑難排解的建議，請參閱：  
  
-   [部署範例](../ide/deployment-examples.md).  
  
-   [疑難排解](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).  
  
## 請參閱  
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [了解 Visual C\+\+ 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)   
 [Windows Installer Deployment](http://msdn.microsoft.com/zh-tw/121be21b-b916-43e2-8f10-8b080516d2a0)