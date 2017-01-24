---
title: "Automation 模型 | Microsoft Docs"
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
  - "Automation [Visual Studio SDK], Automation 模型"
ms.assetid: 48ddc192-96ff-46dc-a1fe-df4eb5c62c84
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Automation 模型
Automation 模型提供擴充 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 之 VSPackage 的替代方式。 這在與擴充性模型相同的舊版 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中是已知問題，Automation 模型是程式設計介面，可讓您存取可驅動整合式開發環境 \(IDE\) 的基礎常式，並可讓您對其進行自訂、調整並自動化。  
  
## VSPackage 和自動化  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] SDK 文件著重於 VSPackage，而其提供的開發可能性高於 Automation 模型。 例如，您可以針對 Automation 模型中的物件撰寫程式碼來自訂語言 \(例如 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]\)。 不過，您無法使用 Automation 模型，以將新的語言加入 IDE。 若要將新的語言加入環境中，您必須開發 VSPackage。  
  
 而且，Automation 模型和 VSPackage 模型會在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中撰寫兩種擴充性方式。 擴充性是增強和擴充 IDE 功能的能力。 自動化指的是使用者所建立的程式碼和工具，可自動化現有環境中的工作，並以程式設計方式驅動 IDE。 相反地，VSPackage 可讓您在 IDE 中加入新的功能。 VSPackage 是可共同建立的物件；亦即，它具有 Class Factory，並讓它自己可供 IDE 使用，方法是實作介面 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>。  
  
 增益集和精靈使用 Automation 模型，以利用其自動化介面來控制或擴充 IDE 的功能。 一般而言，Microsoft 會包含許多增益集與 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。 您可以使用增益集來整合工具列和功能表上的新命令、加入工具視窗，或自動化您定期在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中執行的特定工作。  
  
 身為 VSPackage 開發人員，您應該參與 Automation 模型。 例如，如果使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] SDK 將新的語言加入 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，則您的語言應該提供強固的程式碼模型，以擴充預先存在的程式碼模型。 如需詳細資訊，請參閱[提供 Automation 模型](../Topic/Contributing%20to%20the%20Automation%20Model.md)。  
  
## 請參閱  
 [Vspackage](../Topic/VSPackages.md)   
 [提供 Automation 模型](../Topic/Contributing%20to%20the%20Automation%20Model.md)