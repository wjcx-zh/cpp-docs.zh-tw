---
title: "狀態持續性支援 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "狀態持續性, Managed 封裝架構支援"
  - "Managed 封裝架構, 狀態持續性支援"
  - "狀態, 持續性"
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# 狀態持續性支援
[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]可以維護通用物件的狀態。  比方說，方案和專案的屬性會儲存，並從方案和專案檔還原。  可以匯出至使用者的設定，並將其從設定檔匯入。  
  
 VSPackages 項目通常仰賴於本機存放區，在系統登錄或目前的使用者或電腦的應用程式資料資料夾中。  需要少量的空間來儲存，例如整數和字串的值通常會儲存在系統登錄中。  存放裝置，諸如點陣圖，需要許多區域的值會儲存在檔案中。  檔案的路徑可以本身儲存在登錄中。  持續性機制必須存取本機存放區的權限。  
  
## 尋找本機存放裝置的支援  
 <xref:Microsoft.VisualStudio.Shell.Package>類別會提供支援，以尋找在目前的使用者或電腦的系統登錄或應用程式資料資料夾中的狀態資訊。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 傳回本機電腦的登錄根目錄路徑[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，例如，HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\8.0Exp。  
  
 本機登錄根目錄取自<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>服務。  如果這是無法使用，它取自<xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> VSPackage 的屬性。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 傳回目前使用者 \(每部電腦\) 之路徑的登錄根目錄[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，例如，HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp。  
  
 本機登錄根目錄取自<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>服務。  如果這是無法使用，它被取自 VSPackage 的 DefaultLocalRegistryRoot 屬性。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 傳回表示做為通用儲存機制的目錄路徑[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]目前漫遊使用者資料，例如 C:\\Documents 和 Settings\\*YourAccountName*\\Application Data\\Microsoft\\VisualStudio\\8.0Exp。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 傳回表示做為通用儲存機制的目錄路徑[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]目前非漫遊使用者的資料，例如 「 C:\\Documents 」 和 「 Settings\\*YourAccountName*\\Local Settings\\Application Data\\Microsoft\\VisualStudio\\8.0Exp。  
  
## 請參閱  
 [VSPackage 狀態](../misc/vspackage-state.md)