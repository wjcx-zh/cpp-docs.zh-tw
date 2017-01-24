---
title: "安裝和部署常見問題集 | Microsoft Docs"
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
  - "部署 [Visual Studio SDK]"
  - "LCID [Visual Studio SDK]"
  - "安裝 [Visual Studio SDK]"
ms.assetid: 4ac62bf3-e335-4899-9074-89bcd004dc65
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# 安裝和部署常見問題集
這個主題提出問題從[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]使用者社群，有關安裝和部署。  主題仍會更新為新社群的內容。  
  
## 內容  
  
-   [以程式設計方式判斷的 LCID 的 Visual Studio 的安裝](#DeterminingtheLCIDofaVisualStudioInstallationProgrammatically)  
  
##  <a name="DeterminingtheLCIDofaVisualStudioInstallationProgrammatically"></a> 以程式設計方式判斷的 LCID 的 Visual Studio 的安裝  
 **問：** 有什麼方法，以程式設計方式判斷的 LCID [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安裝嗎?  
  
 **A：** <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale2.GetUILocale%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale.GetUILocale%2A>將傳回的 LCID [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]目前使用中。  
  
## 請參閱  
 [發行產品](../misc/releasing-a-visual-studio-integration-product.md)