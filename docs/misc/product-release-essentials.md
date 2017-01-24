---
title: "產品版本基本項目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "部署, 基本項目"
  - "安裝 [Visual Studio SDK], 基本項目"
ms.assetid: 28370bc8-f3a7-4c5e-9b35-8331cda14ff4
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 產品版本基本項目
愉快且穩固的安裝經驗會形成使用者對 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合產品的持久印象。 不愉快的安裝經驗也會形成持久印象，因此下列安裝開發和測試最佳做法值得投資。  
  
## 開發 Windows Installer 安裝程式封裝  
 Windows Installer 是適用於 Windows 和 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合產品的建議安裝和組態服務。  
  
> [!NOTE]
>  安裝 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合產品的 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 文件是根據 Windows Installer 概念所建置，但未涵蓋 Windows Installer 本身。 如需 Windows Installer 文件相關章節的連結，請參閱下表。  
  
 在安裝內容中，*「元件」*\(component\) 指的是 Windows Installer 元件。 元件包含資源 \(例如檔案和登錄項目\) 並以一個單位進行安裝和移除。  
  
|工作|如需詳細資訊，請參閱|  
|--------|----------------|  
|深入了解 Windows Installer。|[Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx)|  
|判斷 VSPackage 的系統需求。|-   [偵測系統需求](../Topic/Detecting%20System%20Requirements.md)|  
|了解如何在安裝封裝中註冊 VSPackage。|-   [VSPackage 註冊](../Topic/VSPackage%20Registration.md)<br />-   [必須在安裝後執行的命令](../Topic/Commands%20That%20Must%20Be%20Run%20After%20Installation.md)|  
|請參閱範例安裝封裝。|-   IronPython 整合安裝範例|  
  
## 支援並存產品  
 「並存」\(side\-by\-side\) \(有時會縮短為 *SxS*\) 指的是同時安裝甚至執行相同產品之多個版本的能力。 針對 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合產品，它也是指 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 本身支援並存的事實。  
  
|工作|如需詳細資訊，請參閱|  
|--------|----------------|  
|了解支援 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合產品中 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的多個版本。|-   [選擇 \[共用和版本建立 Vspackage](../Topic/Choosing%20Between%20Shared%20and%20Versioned%20VSPackages.md)<br />-   [管理元件](../Topic/Component%20Management.md)|  
|了解支援 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合產品的多個版本。|-   [選擇 \[共用和版本建立 Vspackage](../Topic/Choosing%20Between%20Shared%20and%20Versioned%20VSPackages.md)<br />-   [註冊副檔名的並存部署](../Topic/Registering%20File%20Name%20Extensions%20for%20Side-By-Side%20Deployments.md)<br />-   [偵測系統需求](../Topic/Detecting%20System%20Requirements.md)<br />-   [必須在安裝後執行的命令](../Topic/Commands%20That%20Must%20Be%20Run%20After%20Installation.md)|  
  
## 測試 Visual Studio 整合產品  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合測試 \(VSIT\) 套件是一系列的測試，可確認 VSPackage 正確地整合至 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。 VSIT 不會測試 VSPackage 的功能，但可協助確保 VSPackage 不會對其他 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 功能造成不良影響。 如需詳細資訊，請參閱 [Visual Studio 整合測試](http://msdn.microsoft.com/zh-tw/8d741735-7d93-46c2-ab93-01da7a0e016d)。