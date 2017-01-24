---
title: "Visual Studio SDK 和 Managed 程式碼 | Microsoft Docs"
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
  - "VSIP, 關於 Managed 程式碼"
ms.assetid: 16b3d88e-b5d8-49a5-a5d7-07cbb0b7e4fc
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Visual Studio SDK 和 Managed 程式碼
*Managed 程式碼*是通用語言執行階段 \(CLR\)，為目標的任何語言所撰寫的程式碼，例如[!INCLUDE[vbprvb](../Token/vbprvb_md.md)]， [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]，或[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]。  無論它以撰寫語言中，所有 managed 程式碼會編譯到 Microsoft 中繼語言 \(MSIL\)，而非原生程式碼。  
  
## 受管理的 VSPackages 的環境支援  
 若要支援建立 VSPackage 或類似的專案與受管理的語言[!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]、 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]提供下列：  
  
-   [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Interop 組件，它可讓 VSPackages 以 managed 程式碼撰寫交互操作不受管理 \(COM\) 與[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\)。  如需詳細資訊，請參閱 [使用 Visual Studio Interop 組件](../Topic/Using%20Visual%20Studio%20Interop%20Assemblies.md)。  
  
-   一組管理套件架構 \(MPF\) 類別，可提供較高階的抽象概念，用於[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE。  這些類別封裝部分最常使用的介面與型別，在[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] interop 組件。  它們會大幅降低提供 VSPackage 或專案的基本功能，您必須執行的工時量。  如需詳細資訊，請參閱 [Managed 封裝架構類別](../misc/managed-package-framework-classes.md)。  
  
-   一組基本的 VSPackage 範例以 managed 程式碼撰寫。  受管理的範例建置簡單、 功能完整的 VSPackage，以示範基本的編輯器、 工具視窗、 物件的擴充項，以及其他元件的範例。  如需詳細資訊，請參閱 [VSSDK 範例](../misc/vssdk-samples.md)。  
  
## 請參閱  
 [Managed VSPackage](../misc/managed-vspackages.md)   
 [使用 Visual Studio Interop 組件](../Topic/Using%20Visual%20Studio%20Interop%20Assemblies.md)   
 [Managed 封裝架構類別](../misc/managed-package-framework-classes.md)