---
title: "部署原生桌面應用程式 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "部署應用程式 [C++]"
  - "應用程式部署 [C++]"
  - "Visual C++, 應用程式部署"
  - "應用程式部署 [C++], 關於應用程式部署"
  - "部署應用程式 [C++], 關於部署應用程式"
  - "散發應用程式 [C++]"
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 部署原生桌面應用程式 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

部署是指用來散發已完成的應用程式或元件，以便在其他電腦上進行安裝的程序。 當應用程式在開發人員的電腦上完成建立時，即開始部署規劃。 當應用程式已安裝並準備在使用者的電腦上執行時，即結束部署。  
  
 Visual Studio 提供各種不同的技術來部署 Windows 應用程式。 這些技術包括 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 部署和 Windows Installer 部署。  
  
-   [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 可用來部署以 Common Language Runtime \(CLR\) 為目標的 C\+\+ 應用程式，CLR 是混合、純粹且和可驗證的組件。 雖然您可以使用 Windows Installer 來部署 Managed 應用程式，但建議您使用 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 以利用.NET Framework 安全性功能，例如資訊清單簽署。[!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 不支援原生 C\+\+ 應用程式的部署。 如需詳細資訊，請參閱 [Visual C\+\+ 應用程式的 ClickOnce 部署](../ide/clickonce-deployment-for-visual-cpp-applications.md)。  
  
-   Windows Installer 技術可用來部署原生 C\+\+ 應用程式或以 CLR 為目標的 C\+\+ 應用程式。  
  
 本文下一節所提供的文章，討論如何確保原生 Visual C\+\+ 應用程式在提供支援之目標平台的任何電腦上執行；您必須在安裝套件中包含哪些檔案；以及轉散發應用程式相依元件的建議做法。  
  
## 在本節中  
 [Visual C\+\+ 中的部署](../ide/deployment-in-visual-cpp.md)  
  
 [部署概念](../ide/deployment-concepts.md)  
  
 [了解 Visual C\+\+ 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)  
  
 [決定要轉散發哪些 DLL](../ide/determining-which-dlls-to-redistribute.md)  
  
 [選擇部署方法](../ide/choosing-a-deployment-method.md)  
  
 [轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)  
  
 [部署範例](../ide/deployment-examples.md)  
  
 [轉散發 Web 用戶端應用程式](../ide/redistributing-web-client-applications.md)  
  
 [Visual C\+\+ 應用程式的 ClickOnce 部署](../ide/clickonce-deployment-for-visual-cpp-applications.md)  
  
 [在舊版執行階段版本上執行 C\+\+ \/clr 應用程式](../ide/running-a-cpp-clr-application-on-a-previous-runtime-version.md)  
  
## 相關章節  
 [建置 C\/C\+\+ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
  
 [部署](../Topic/Deploying%20the%20.NET%20Framework%20and%20Applications.md)  
  
 [疑難排解](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)