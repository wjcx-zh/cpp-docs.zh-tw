---
title: "升級專案項目 | Microsoft Docs"
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
  - "升級專案項目"
  - "專案 [Visual Studio SDK], 升級項目"
  - "專案項目 [Visual Studio], 升級"
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 升級專案項目
如果您新增或管理您不會實作專案系統內的項目時，您可能需要參與專案的升級程序。  詳細報告是可以加入至專案系統的某個項目的範例。  
  
 一般而言，專案項目實作者要運用已完全執行個體化，而且已升級的專案，因為他們需要知道會參考哪一個專案以及有其他專案屬性有進行升級的決策。  
  
### 取得專案升級通知  
  
1.  設定<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> \(vsshell80.idl 中所定義\) 的旗標在您的專案項目實作。  這會使您的專案項目 VSPackage 自動載入時[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]殼層會決定專案系統會在升級的過程中。  
  
2.  宣布<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>介面透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>方法。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>介面之後，專案系統執行已經完成升級作業，並建立新的升級的專案時，就會引發。  視案例而定， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>介面之後，會引發<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>，或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>方法。  
  
### 若要升級的專案項目檔案  
  
1.  您仔細必須在您的專案項目實作，來管理檔案的備份程序。  這特別適用於並排顯示備份時，其中`fUpgradeFlag`參數的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法已設為<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>、 以及端指定為".old"的檔案具有已備份的檔案放置的位置。  備份的檔案的時限系統時間已在升級專案時可以被指定為過時。  此外，它們可能會覆寫除非您採取特定動作來防止這種情形。  
  
2.  在您的專案項目取得的專案升級時，通知 **Visual Studio 的轉換精靈**仍會顯示。  因此，您應該使用的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>升級訊息提供精靈使用者介面的介面。  
  
## 請參閱  
 [Visual Studio Conversion Wizard](http://msdn.microsoft.com/zh-tw/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [升級自訂專案](../misc/upgrading-custom-projects.md)