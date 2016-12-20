---
title: "使用自動化建立選項頁面 | Microsoft Docs"
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
  - "[工具選項] 頁面 [Visual Studio SDK], 建立"
  - "自動化 [Visual Studio SDK], 建立 [工具選項] 頁面"
ms.assetid: 05ec0337-58fe-4746-8e85-7fb97f285522
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 使用自動化建立選項頁面
受管理的 VSPackages 可以用來擴充自動化[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\) 藉由新增**選項**分頁成**工具**功能表。  
  
 A **工具選項**頁面基本上是使用者控制項，並且會編碼為任何其他的使用者控制項一樣。  一般而言，您可使用的其中一個[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 的設計工具建立的物件，並將使用者控制項。  
  
> [!NOTE]
>  **工具選項**實作為對話方塊的頁面\] 方塊中，使用`DialogProc`來處理 windows 訊息，必須為非強制回應對話方塊，千萬不要呼叫`EndDialog`函式。  
  
 您應該使用 VSPackage 提供對環境的自動化物件來支援使用者控制項屬性。  
  
## 工具選項頁使用 Interop 組件實作的自動化支援  
 若要支援自動化模型，VSPackage 必須建立並註冊自動化物件。  如需詳細資訊，請參閱 [提供自動化的 Vspackage](../Topic/Providing%20Automation%20for%20VSPackages.md)。  
  
 當使用自動化模型的程式碼會呼叫`DTE.Properties`屬性集合的指定**工具選項** \] 頁面上，IDE 會使用 VSPackage 的實作所提供的 automation 物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> ，傳回集合，並允許存取其組成<xref:EnvDTE.Property>物件。  
  
 **附註**所傳回的自動化物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>而定 \(如 VSPackage 可以支援一個以上的自動化物件\) 所提供的 GUID。  如需有關如何實作 automation 物件的詳細資訊，請參閱[在選項頁面的自動化支援](../Topic/Automation%20Support%20for%20Options%20Pages.md)。  
  
 A **工具選項**頁面由兩個識別項指定。  第一的識別項是字串，表示包含這個項目上的資料夾**選項** 一節的 **工具**功能表。  第二個識別項是字串，表示資料夾中的特定項目。  如需詳細資訊，請參閱 [使用選項頁](../misc/using-options-pages.md)。  
  
 兩個登錄項目時需要註冊自動化物件：  
  
-   在 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< 版本* \\Packages\\*\<PackageGUID\>*\\Automation  
  
-   在 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\AutomationProperties  
  
     其中 *\<Version\>* 版本的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] \(例如，8.0\) 和 *\<PackageGUID\>* VSPackage 實作 automation 物件的 guid。  
  
 取決於在 AutomationProperties 登錄項目的狀態下設定**工具選項**頁面可能會自動儲存並且還原到[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定機制，當使用者選取**匯入\/匯出設定**命令**工具**功能表。  如需有關儲存**工具選項**頁面設定，請參閱[註冊工具選項頁面](../misc/registering-custom-options-pages.md)。  
  
 應用程式可能不使用 automation 模型來實作支援**工具選項**網頁的內容及設定值。  
  
 這可能需要幾個原因：  
  
-   設定由**工具選項**頁面是單純在結構中的相對較一般的自動化內容模型的支援。  
  
-   若要防止其他應用程式無法以程式設計方式管理需要其**工具選項**頁面。  
  
-   特殊的存取控制或安全性功能是必要的。  
  
 在這些情況下，都可以實作 VSPackages **工具選項**頁以任何方式所適用的支援。  不過，它們必須：  
  
-   處理的設定值**工具選項**頁面內容。  
  
-   管理的保存性**工具選項**頁面透過狀態[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定。  
  
-   提供一套 API，必要時，其他的應用程式，可以使用**工具選項**頁面。  
  
 內容的**字型和色彩** 對話方塊是一個範例 **工具選項**無法修改透過自動化模型的頁面。  相反地，提供不同的 API，根據<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>介面，以允許以程式設計方式操作的**字型和色彩工具選項**頁面。  如需有關控制**字型和色彩工具選項**頁面上，請參閱[使用字型和色彩](../Topic/Using%20Fonts%20and%20Colors.md)。  
  
## 工具選項頁，在受管理的封裝架構中的自動化支援  
 設定<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A>的登錄實作的屬性， <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> ，以表示您的執行個體的管理套件架構基底實作**工具選項**頁面支援自動化。  
  
 **工具選項**頁面衍生自<xref:Microsoft.VisualStudio.Shell.DialogPage>會提供預設的自動化物件，來覆寫。  
  
 如果**工具選項** 頁面實作不支援自動化，實作必須提供自己的 API，以允許以程式設計方式存取 **工具選項**頁面。  
  
> [!NOTE]
>  IDE 的**字型和色彩** 頁面是範例 **工具選項** 不支援自動化，但可存取的網頁 **工具選項**逐頁查看自己的 API。  如需詳細資訊，請參閱 [使用字型和色彩](../Topic/Using%20Fonts%20and%20Colors.md)。  
  
## 請參閱  
 [擴充 Visual Studio 環境](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)   
 [使用 Interop 組件建立選項頁面](../misc/creating-options-pages-by-using-interop-assemblies.md)   
 [建立選項頁](../Topic/Creating%20Options%20Pages.md)   
 [如何：建立自訂選項頁面](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)   
 [在選項頁面的自動化支援](../Topic/Automation%20Support%20for%20Options%20Pages.md)   
 [使用選項頁](../misc/using-options-pages.md)