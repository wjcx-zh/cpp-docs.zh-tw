---
title: "Visual C++ 應用程式的 ClickOnce 部署 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "部署應用程式 [C++]，ClickOnce"
  - "應用程式部署 [C++]，ClickOnce"
  - "ClickOnce 部署 [C++]，C++ 應用程式"
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Visual C++ 應用程式的 ClickOnce 部署
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 提供了部署 Windows 應用程式的兩種不同技術：ClickOnce 部署或 [Windows Installer](http://msdn.microsoft.com/library/cc185688) 部署。  
  
## C\+\+ 中的 ClickOnce 部署  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 部署環境不直接支援使用 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 專案，但是有提供工具可使用它。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 不支援 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 開發環境中的 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)]。  如果 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 是 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 專案的相依專案，您就可以從 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 開發環境使用 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 部署來發行應用程式 \(包括它的相依性\)。  
  
 若要使用 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 應用程式，首先您必須使用[Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md) 或它的圖形化使用者介面版本 \(如需詳細資訊，請參閱[MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)\) 建置 [ClickOnce 應用程式資訊清單](../Topic/ClickOnce%20Application%20Manifest.md) 和 [ClickOnce 部署資訊清單](../Topic/ClickOnce%20Deployment%20Manifest.md)。  
  
 請先使用 Mage.exe 建置應用程式資訊清單，產生的檔案會有 .manifest 的副檔名。  接著，使用 Mage.exe 建置部署資訊清單，而產生的檔案會有 .application 的副檔名。  然後，簽名資訊清單。  
  
 應用程式資訊清單必須指定目標處理器 \(\[**x86**\]、\[**x64**\] 或 \[**ARM**\]\)。  如需這些選項的詳細資訊，請參閱[64 位元應用程式的部署必要條件](../Topic/Deploying%20Prerequisites%20for%2064-bit%20Applications.md)。  
  
 此外，應用程式和部署資訊清單的名稱必須與 C\+\+ 應用程式的名稱不同。  這可避免 Mage.exe 所建立的應用程式資訊清單，與屬於 C\+\+ 應用程式一部分的外部資訊清單發生衝突。  
  
 您的部署將需要安裝應用程式所依賴的任何 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫。  若要判斷特定應用程式的相依性，您可以搭配 \/DEPENDENTS 選項使用 depends.exe 或 DUMPBIN 公用程式。  如需相依性的詳細資訊，請參閱[了解 Visual C\+\+ 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。  您可能必須執行 VCRedist.exe，這個公用程式會在目標電腦中安裝 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫。  
  
 此外，您可能還需要為應用程式建置啟動載入器 \(Bootstrapper\) \(必要條件安裝程式\)，以部署必要條件元件。如需啟動載入器的詳細資訊，請參閱[建立啟動載入器套件](../Topic/Creating%20Bootstrapper%20Packages.md)。  
  
 如需這項技術的詳細描述，請參閱 [ClickOnce 安全性和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)。  如需詳細的 [!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 部署範例，請參閱[逐步解說：手動部署 ClickOnce 應用程式](../Topic/Walkthrough:%20Manually%20Deploying%20a%20ClickOnce%20Application.md)。  
  
## 請參閱  
 [Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)   
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [部署應用程式、服務和元件](../Topic/Deploying%20Applications,%20Services,%20and%20Components.md)   
 [Windows Installer Deployment](http://msdn.microsoft.com/zh-tw/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [ClickOnce 安全性和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)   
 [建立啟動載入器套件](../Topic/Creating%20Bootstrapper%20Packages.md)   
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)