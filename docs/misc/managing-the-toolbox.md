---
title: "管理工具箱 | Microsoft Docs"
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
  - "工具箱 [Visual Studio SDK], 自動索引標籤選取"
  - "工具箱 [Visual Studio SDK], 管理"
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
caps.handback.revision: 33
manager: "douge"
---
# 管理工具箱
[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 可讓 VSPackage \(例如編輯器或設計工具\) 管理 \[工具箱\] 的成員資格和外觀。  
  
 此外，\[工具箱\] 本身可以使用自動化進行管理。 如需透過自動化管理工具箱的詳細資訊，請參閱[如何：控制工具箱](../Topic/How%20to:%20Control%20the%20Toolbox.md)。  
  
## 自動工具箱索引標籤選取  
 只有特定 \[工具箱\] 索引標籤或類別才能根據編輯器或設計工具目前哪個為使用中而自動成為使用中。 例如，如果已啟動表單設計工具，您可能會想要選取 \[所有 Windows Forms\] 索引標籤。  
  
 這項支援僅限於需要執行下列動作的編輯器和設計工具：  
  
1.  實作 Factory 物件，以提供編輯器或設計工具的執行個體。 如需實作設計工具或編輯器 Factory 物件的詳細資訊，請參閱[編輯器 Factory](../Topic/Editor%20Factories.md)。  
  
2.  註冊 \[工具箱\] 索引標籤，而這個索引標籤會在編輯器或設計工具存在時自動啟動。  
  
## 控制工具箱  
 補充自動化支援，[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 提供下列介面讓 VSPackages 可更進一步地控制 \[工具箱\] 的管理方式。  
  
|介面|描述|  
|--------|--------|  
|<xref:System.Drawing.Design.IToolboxService>|可讓應用程式從 \[工具箱\] 中管理、加入和移除 <xref:System.Drawing.Design.ToolboxItem> 物件。 也會啟用外觀和 \[工具箱\] 類別的設定。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|可讓應用程式管理、加入和移除主動型 \[工具箱\] 控制項，以及設定 \[工具箱\] 類別和外觀。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|透過提供完整的持續性和當地語系化支援，來擴充 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 中找到的功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 使用這些介面時，請記住幾個重點：  
  
-   只有 Managed Package Framework 型 VSPackage 才能使用 <xref:System.Drawing.Design.IToolboxService>。  
  
-   使用 <xref:System.Drawing.Design.IToolboxService>，無法將控制項直接加入 \[工具箱\]。  
  
-   VSPackage 必須使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 來加入控制項，或是將控制項裝載在衍生自 <xref:System.Windows.Forms.AxHost> 的包裝函式控制項中。  
  
     Visual Studio 提供 `Aximp.exe` 工具，來自動化在衍生自 <xref:System.Windows.Forms.AxHost> 之控制項中的 ActiveX 控制項包裝。 如需詳細資訊，請參閱[Aximp.exe \(Windows Forms ActiveX Control Importer\)](../Topic/Aximp.exe%20\(Windows%20Forms%20ActiveX%20Control%20Importer\).md)。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 是可透過 Interop 組件使用的 COM 型介面。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 衍生自 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>，並實作它的所有方法。  
  
     只能在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 的執行個體中取得物件。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 未衍生自 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>也未實作它的方法。  
  
     需要這兩個介面中功能的物件必須從環境中取得這兩個介面的執行個體。  
  
-   使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 時，索引標籤正式 \(非當地語系化\) 名稱的相關資訊是透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> 方法所處理。  
  
-   使用 <xref:System.Drawing.Design.IToolboxService> 時，是由實作者負責管理當地語系化資訊 \(例如類別名稱\)。  
  
 使用設定機制，讓使用者可以透過 IDE \[工具\] 功能表上的 \[匯入\/匯出設定\] 命令來儲存使用者所存取的 \[工具箱\] 設定。 如需如何使用設定的詳細資訊，請參閱[擴充使用者設定和選項](../Topic/Extending%20User%20Settings%20and%20Options.md)。  
  
## 請參閱  
 [擴充工具箱](../misc/extending-the-toolbox.md)