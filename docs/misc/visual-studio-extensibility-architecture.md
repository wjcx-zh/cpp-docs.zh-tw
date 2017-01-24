---
title: "Visual Studio 擴充性架構 | Microsoft Docs"
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
  - "Visual Studio, 環境模型"
  - "環境模型, Visual Studio"
ms.assetid: 280fdb55-3e70-41fd-8da0-4039bf5d4894
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# Visual Studio 擴充性架構
[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\) 是一種架構裝載 VSPackages，並使交換共用的服務的工作變得更容易。  舉例而言，這是 IDE 會實作使用者介面 \(UI\) 的方式。  IDE 提供容器視窗的預設工具列和功能表。  它也提供了豐富的 COM 基礎架構，讓可程式化的 UI。  完整的命令處理和路由配置，讓使用者開放式架構讓讓您輕鬆存取這兩個現有的安裝與命令集。  
  
## 擴充性架構  
 下圖顯示[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]的擴充架構。  請注意軟體應用程式的概念不存在。  相反地，IDE 主機軟體元件會呼叫 VSPackages，可提供應用程式功能。  這項功能，這反而是在 IDE 之間當成共用服務。  VSPackages 提供服務的這些以及其他的 VSPackages。  標準的 IDE 也提供各式各樣的服務，例如<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>，讓您存取的 IDE 視窗化功能。  
  
 ![環境架構圖形](../misc/media/environment.png "environment")  
Visual Studio 的架構的 \[一般化\] 檢視  
  
 請注意 VSPackages 和服務之間的關係是雙向。  VSPackages 使用由其他人所提供的服務，雖然它們也可以提供服務本身所使用的<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>介面。  此服務為基礎的架構成長超出 Microsoft ActiveX 設計工具實作中，服務是一群相關的介面執行工作。  從嚴格的 「 COM 觀點來看，必須在單一的 COM 類別中實作的特定服務的所有介面。  
  
 標準的 IDE 提供了重要的服務，例如<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>， <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>，以及<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>，這由 VSPackages。  下表列出並描述一些在這些服務。  如需詳細資訊，請參閱 [使用並提供服務](../Topic/Using%20and%20Providing%20Services.md)。  
  
|IDE 服務|描述|  
|------------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|提供對 IDE 存取基本功能、 VSPackages，與登錄服務處理。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本的視窗和 UI 相關的功能，在 IDE 中，例如建立工具和文件視窗的能力。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供基本與方案相關的功能，例如列舉專案、 建立新的專案，並監控專案變更的能力。|  
  
 因為它們的共用服務，產生互動的緊密整合的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 和 VSPackages 都是緊密的互相依存。  不過，儘管其密切互動它們具有不同的責任。  
  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 負責下列工作：  
  
-   提供重要的服務，供外部的 VSPackages。  
  
-   提供可程式化的介面，以便與標準的 UI 項目的參與。  
  
-   正在建立 VSPackages 的執行的個體，視需要由使用者動作或其他 VSPackages 要求的服務。  
  
-   提供可讓通訊和 VSPackages 之間的協調的服務。  
  
-   管理方案和其所需的檔案。  
  
-   提供視窗管理。  
  
-   提供路由命令和命令列，例如功能表、 工具列和快顯功能表。  
  
-   選取範圍、 內容和貨幣協調。  
  
 VSPackages 負責下列工作：  
  
-   執行特定的初始化和終止常式。  
  
-   將資訊寫入至登錄中，IDE 會使用來載入適當的 VSPackages，在適當的時機。  
  
-   提供服務所需的通訊與其他的 VSPackages。  
  
-   針對新的專案類型、 編輯器或設計工具中提供實作。  
  
-   提供內建的 UI 項目，例如工作項目、 工具箱項目，以及 \[選項\] 對話方塊中的擴充功能。  
  
## 請參閱  
 [Visual Studio Shell](../Topic/Visual%20Studio%20Shell.md)   
 [Vspackage](../Topic/VSPackages.md)   
 [使用並提供服務](../Topic/Using%20and%20Providing%20Services.md)   
 [如何: 取得服務](../Topic/How%20to:%20Get%20a%20Service.md)