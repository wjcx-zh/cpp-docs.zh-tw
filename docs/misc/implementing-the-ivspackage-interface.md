---
title: "實作 IVsPackage 介面 | Microsoft Docs"
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
  - "IVsPackage 介面"
  - "介面, 實作 IVsPackage"
ms.assetid: 0c76b2e1-ce63-47fc-93ee-847cad281fc1
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 實作 IVsPackage 介面
必須實作所有的 VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>介面。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]呼叫類別的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>若要初始化和關閉 VSPackages，以取得相關聯的屬性頁，因為其他原因。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>介面是閘道介面之間[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]和 VSPackage。  
  
 您可以將受管理的 VSPackage 寫成的子類別<xref:Microsoft.VisualStudio.Shell.Package>類別，就會有哪些實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>代表您。  如需詳細資訊，請參閱 [Managed VSPackage](../misc/managed-vspackages.md)。  
  
> [!NOTE]
>  最多不受管理的範例程式碼，Visual Studio 的整合部分中的[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]以現用樣板程式庫 \(ATL\)。  您不需要使用 ATL 來建立 VSPackages，但您必須了解 ATL，若要了解範例程式碼。  
  
## 請參閱  
 [Vspackage](../Topic/VSPackages.md)