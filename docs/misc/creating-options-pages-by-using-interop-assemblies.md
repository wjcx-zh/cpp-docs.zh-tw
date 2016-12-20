---
title: "使用 Interop 組件建立選項頁面 | Microsoft Docs"
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
  - "工具選項頁面 [Visual Studio SDK], 使用 Interop 組件建立"
  - "Interop 組件, 建立工具選項頁面"
ms.assetid: 7a03f2f5-a53e-4a46-877f-5b10dd82dbc3
caps.latest.revision: 30
caps.handback.revision: 30
manager: "douge"
---
# 使用 Interop 組件建立選項頁面
Managed VSPackage 可以將 \[選項\] 頁面加入 \[工具\] 功能表中，以使用 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 的 COM Interop 組件來擴充 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合式開發環境 \(IDE\)。  
  
 \[工具選項\] 頁面基本上是一個使用者控制項，而且編碼方式與任何其他使用者控制項相同。 您一般會使用其中一個 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 的設計工具來建立物件以及加入使用者控制項。  
  
> [!NOTE]
>  使用 DialogProc 來處理 Windows 訊息且實作為對話方塊的 \[工具選項\] 頁面必須是非強制回應對話方塊，而且不得呼叫 EndDialog 函式。  
  
 您應該使用 VSPackage 提供給環境的 Automation 物件，以支援使用者控制項所顯示的屬性。  
  
 實作 \[工具選項\] 頁面的 VSPackage，可以支援直接透過程式設計方式或透過 IDE 的 Automation 模型來控制其屬性。 如需支援具有 Automation 之 \[工具選項\] 頁面的詳細資訊，請參閱 [使用自動化建立選項頁面](../misc/creating-options-pages-by-using-automation.md)。  
  
## 將工具選項頁面提供給 IDE  
 除了實作使用者控制項之外，VSPackage 還必須將該控制項提供給 IDE。  
  
 這是透過實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法來完成，而此方法根據傳遞的 GUID 來傳回 <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE> 結構。  
  
 IDE 使用 <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE> 結構來設定 \[屬性\] 頁面的特性。  
  
 其 `dwFlags` 成員中所含的設定決定其他 <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE> 成員的確切解譯。 結構一般會提供：  
  
-   從中載入圖示或字串資源之執行個體的控制代碼。  
  
-   頁面之對話方塊範本的資源識別項。  
  
-   頁面的 DialogProc 指標。  
  
## 註冊工具選項頁面  
 您可以在下列登錄位置中建立項目，以註冊 \[工具選項\] 頁面：HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<版本\>*\\ToolsOptionsPages，其中 *\<版本\>* 是 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的版本 \(如 8.0\)。  
  
 若要註冊頁面，您可以手動編輯登錄，或使用登錄指令碼 \(.rgs 檔案\)。 如需詳細資訊，請參閱[Creating Registrar Scripts](../atl/creating-registrar-scripts.md)。  
  
## 請參閱  
 [擴充 Visual Studio 環境](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)   
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)   
 [在選項頁面的自動化支援](../Topic/Automation%20Support%20for%20Options%20Pages.md)   
 [使用選項頁](../misc/using-options-pages.md)   
 [建立選項頁](../Topic/Creating%20Options%20Pages.md)   
 [使用自動化建立選項頁面](../misc/creating-options-pages-by-using-automation.md)