---
title: "品牌概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "關於對話方塊"
  - "VSPackage, 啟動顯示畫面"
  - "VSPackage, 品牌"
ms.assetid: a47b3645-574c-41c7-8a97-d071cd6b1e82
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# 品牌概觀
若要在開頭顯示畫面中顯示產品資訊或**詳見 \[說明**對話方塊中，您的 VSPackage 必須下列其中一個：  
  
-   提供 InstalledProducts 登錄機碼下的詳細的產品資訊。  
  
     \-或\-  
  
-   實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>  
  
 受管理的封裝架構 \(MPF\) 提供<xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute>屬性，以控制 InstalledProducts 登錄機碼下的登錄。  如需詳細資訊，請參閱 [如何：設定 VSPackage 的品牌 \(C\# 和 Visual Basic\)](../misc/how-to-brand-a-vspackage-csharp-and-visual-basic.md)。  
  
 Visual Studio 的程式庫提供`IVsInstalledProductImpl`範本類別的實作建立<xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>。  如需詳細資訊，請參閱 [如何：設定 VSPackage 的品牌 \(C\+\+\)](../misc/how-to-brand-a-vspackage-cpp.md)。  
  
 實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>明確會比使用 \[屬性\] 或 \[範本更具威力。  
  
-   您可以指定不同於一個開頭顯示畫面圖示**詳見 \[說明**圖示。  
  
-   您可以指定開頭顯示畫面產品名稱，且有別於**詳見 \[說明**產品名稱。  
  
    > [!IMPORTANT]
    >  如果您使用<xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> ，也實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>，優先順序較高的介面。  
  
    > [!NOTE]
    >  相同的圖示資源可用於啟動顯示畫面和**詳見 \[說明**對話方塊。  您的 VSPackage 圖示資源應該包含啟動顯示畫面的 16 × 16 映像，以及 32 × 32 影像，以**詳見 \[說明**對話方塊。  如果您提供只能有一個影像大小，將會視需要調整大小，但視覺的結果就是不理想。  
  
 如需相關工作的清單，請參閱[Vspackage](../Topic/VSPackages.md)。  
  
## 請參閱  
 [Vspackage](../Topic/VSPackages.md)   
 [Visual Studio Library 概觀](../misc/visual-studio-library-overview.md)